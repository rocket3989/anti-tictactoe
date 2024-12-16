<script>
	let cellStates = [' ', 'X', 'O'];

	let board = $state([0, 0, 0, 0, 0, 0, 0, 0, 0]);
	let turn = $state(1);
	let winner = $state();
</script>

<div class="gameContainer">
	<div class="board">
		{#each { length: 9 }, i}
			<button 
                class="cell"
                disabled={board[i] !== 0 || winner}
                onclick={() => {board[i] = turn; turn = turn === 1 ? 2 : 1}}
            >
                {cellStates[board[i]]}
            </button>
		{/each}
	</div>
</div>

<style>
	:root {
		--game-size: 250px;
	}
	.gameContainer {
		max-width: 700px;
		margin: 0 auto;
		margin-top: 10px;
		margin-bottom: 40px;
		align-items: center;
		justify-items: center;
	}
	.board {
		display: grid;
		grid-template-columns: 1fr 1fr 1fr;
		grid-template-rows: 1fr 1fr 1fr;
		width: var(--game-size);
		height: var(--game-size);
		border: 1px solid black;
	}
	.cell {
        width: calc(var(--game-size) / 3);
		height: calc(var(--game-size) / 3);
		border: 1px solid black;
		text-align: center;
        vertical-align: middle;
		font-size: calc(var(--game-size) / 3);
        line-height: calc(var(--game-size) / 3);
	}
</style>
