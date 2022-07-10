<script>
	let count = Number(window.localStorage.getItem("count")) ?? 0;
	let testFunc = (n) => {
		if (typeof count === "string") count = Number(count);
		count += n;
		window.localStorage.setItem("count",count);
	};
</script>

<main>
	<div>
		<h1>Mjög einfaldur counter skrifaður í svelte</h1>
		<span>
			<button on:click={() => {testFunc(1)}}>+1</button>
			<button on:click={() => {testFunc(2)}}>+2</button>
			<button on:click={() => {testFunc(5)}}>+5</button>
		</span>
		<span>
			<button on:click={() => {testFunc(-1)}}>-1</button>
			<button on:click={() => {testFunc(-2)}}>-2</button>
			<button on:click={() => {testFunc(-5)}}>-5</button>
		</span>
	</div>
	<div>
		<input bind:value={count}/>
	</div>
</main>

<style>
	:root {
		--clear: rgba(255, 255, 255, 0);
		--background: #562;
		--highlight: #673;
		--text: #fff;
	}

	main {
		display: grid;
		grid-template-columns: 1fr 2fr;
	}

	main div {
		text-align: center;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		gap: 1em;
	}

	span {
		width: 100%;
		display: flex;
		justify-content: space-around;
		gap: 1em;
	}

	button {
		padding: 0.5em;
		font-size: 1.2em;
		border: 2px solid var(--text);
		border-radius: 7px;
		background-color: var(--clear);
		color: white;
		cursor: pointer;
		transition: 0.15s;
	}

	button:hover, button:focus-visible {
		background-color: var(--highlight);
	}

	input {
		text-align: center;
		color: var(--text);
		background-color: var(--clear);
		border: none;
		font-size: 10em;
		max-width: 4em;
		outline: none;
	}
</style>