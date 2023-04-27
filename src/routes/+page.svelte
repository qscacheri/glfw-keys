<script lang="ts">
	import { keys, type GLFWKeyCode } from '../lib/keys';
	let currentKey: GLFWKeyCode | null = null;
	function handleKeyDown(event: KeyboardEvent) {
		currentKey = keys[event.code];
	}
</script>

<main>
	<div class="container">
		{#if currentKey}
			<p>{currentKey.glfwKeyCode}</p>
			<p>{currentKey.glfwName}</p>
		{:else}
			<p>Press a key</p>
		{/if}
	</div>
</main>
<footer>Quin Scacheri</footer>

<svelte:window on:keydown={handleKeyDown} />

<svelte:head>
	<title>GLFW Keys</title>
	<meta name="description" content="A list of GLFW keys" />
</svelte:head>

<style>
	p {
		filter: drop-shadow(0.3rem 0.3rem 0.4rem rgba(0, 0, 0, 0.2));
	}
	.container {
		display: grid;
		place-items: center;
	}
	main {
		font-size: 2rem;
		overflow: hidden;
		font-family: sans-serif;
		color: #333;
		display: grid;
		place-items: center;
		width: 100vw;
		height: 100vh;
	}
	footer {
		font-family: sans-serif;
		position: fixed;
		right: 2rem;
		bottom: 2rem;
		font-size: 0.5rem;
	}
	@media (prefers-color-scheme: dark) {
		main {
			background: #333;
			color: #eee;
		}

		p {
			filter: drop-shadow(0.3rem 0.3rem 0.4rem #ffffff34);
		}
	}
	@media (min-width: 640px) {
		main {
			font-size: 4rem;
		}

		footer {
			font-size: 0.2rem;
		}
	}
</style>
