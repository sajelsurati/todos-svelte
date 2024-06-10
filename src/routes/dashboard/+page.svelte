<script>
    let todoList = ['Do the groceries'];
    let currTodo = "";
    let error = false;
    function addTodo() {
        error = false;
        if (!currTodo) {
            error = true;
        }
        todoList = [...todoList,currTodo];
        currTodo = "";
    }
</script>

<div class = "mainContainer">
    <div class = "headerContainer">
        <h1>Todo List</h1>
        <button>
            <i class="fa-regular fa-floppy-disk"/>
            <p>Save</p>
        </button>
    </div>

    <main>
        {#each todoList as todo, index}
        <div class = "todo">
            <p>
                {index+1}. {todo}
            </p>
            <div class = "actions">
                <i class="fa-regular fa-pen-to-square"/>
                <i class="fa-regular fa-trash-can"/>
            </div>
        </div>
        {/each}
    </main>
    <div class = {"enterTodo " + (error ? 'errorBorder' : '')}>
        <input bind:value = {currTodo} type="text" placeholder="Enter todo"/>
        <button on:click = {addTodo}>ADD</button>
    </div>
</div>

<style>
    .mainContainer {
        display: flex;
        flex-direction: column;
        min-height : 100vh;
        gap: 24px;
        padding: 24px;
        width: 100%;
        max-width: 1000px;
        margin: 0 auto;
    }

    .headerContainer {
        display: flex;
        align-items: center;
        justify-content: space-between;
    }

    .headerContainer button {
        background: #003c5b;
        color: white;
        padding: 10px 18px;
        border: none;
        border-radius: 4px;
        font-weight: 700;
        display: flex;
        align-items: center;
        gap: 10px;
    }

    .headerContainer button i {
        font-size: 1.1rem;
    }

    .headerContainer button:hover {
        opacity: 0.7;
        cursor: pointer;
    }

    main {
        display: flex;
        flex-direction: column;
        gap: 8px;
        flex: 1;
    }

    .todo {
        border-left: 1px solid cyan;
        padding: 8px 14px;
        display: flex;
        align-items: center;
        justify-content: space-between;
    }

    .actions {
        display: flex;
        align-items: center;
        gap: 14px;
        font-size: 1.3rem;
    }

    .actions i:hover {
        color:coral;
    }

    .actions i {
        cursor: pointer;
    }
    
    .enterTodo {
        display: flex;
        align-items: stretch;
        border: 1px solid #0891b2;
        border-radius: 5px;
    }

    .enterTodo input {
        background: transparent;
        border: none;
        padding: 14px;
        color: white;
        flex: 1;
    }

    .errorBorder {
        border-color: coral !important;
    }

    .enterTodo input:focus {
        outline: none;
    }

    .enterTodo button {
        padding: 0 28px;
        background: #003c5b;
        border: none;
        color: cyan;
        font-weight: 600;
        cursor: pointer;
        border-radius: 5px;
        overflow: hidden;
    }

    .enterTodo button:hover {
        background: transparent;
    }

</style>
