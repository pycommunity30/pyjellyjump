<p>pyjellyjump is a game made with python 3/pygame, a still-in-dev, great for structures of many platformer games, there may be a few bugs, you can report it @jerrbearis2cool@gmail.com suport would be great for a developing game, phone version coming soon</p>
<html>
  <img src="mygamelogo.png" alt="logo" width="200" height="200">
</html>
<html>
<style> 
body {
  background-image: url('background.jpg'); 
}
</style>
</html>
<head>
  <script data-ad-client="ca-pub-9568406816158293" async 
  src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
</head>
<html>
  <h1>full edition(1.0.0)</h1>
  <h3>Download code</h3>
</html>
<html>
  <a href="platformer.exe" download>Download code</a>
</html>
<html>
<h3>DOWNLOAD PICTURES</h3>
</html>
<html>
  <a href="playeris2cool-1.png" download>Download player img</a>
</html>
<html>
  <a href="grassiscool-1.png" download>Download grass img</a>
</html> 
<html>
  <p>after downloading all the files put them all into a local file and run the exe</p>
</html>
<html>
  <h1>One download version(0.0.0)</h1>
</html>
<html>
  <h1>Python version(0.0.0)</h1>
<html>
  <h1>credits</h1>
</html>
<html>
  <p>python 3, pycharm, pyinstaller, pygame</p>
</html>
<html>
  <h1>Wait game by kevcore</h1>
<!DOCTYPE html>
<html>
<head>
  <title></title>
  <style>
  html, body {
    height: 100%;
    margin: 0;
  }

  body {
    background: gray;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  canvas {
    border: 10px solid black;
  }
  </style>
</head>
<body>
<span id="count">0</span>
<canvas width="400" height="400" id="game"></canvas>
<script>
var canvas = document.getElementById('game');
var context = canvas.getContext('2d');

var grid = 16;
var count = 0;
  
var snake = {
  x: 0,
  y: 0,
  
  // snake velocity. moves one grid length every frame in either the x or y direction
  dx: grid,
  dy: 0,
  
  // keep track of all grids the snake body occupies
  cells: [],
  
  // length of the snake. grows when eating an apple
  maxCells: 2
};
var apple = {
  x: 320,
  y: 320
};

// get random whole numbers in a specific range
// @see https://stackoverflow.com/a/1527820/2124254
function getRandomInt(min, max) {
  return Math.floor(Math.random() * (max - min)) + min;
}

// game loop
function loop() {
  requestAnimationFrame(loop);

  // slow game loop to 15 fps instead of 60 (60/15 = 4)
  if (++count < 8) {
    return;
  }
  var num = document.getElementById("count");
  count = 0;
  context.clearRect(0,0,canvas.width,canvas.height);

  // move snake by it's velocity
  snake.x += snake.dx;
  snake.y += snake.dy;

  // wrap snake position horizontally on edge of screen
  if (snake.x < 0) {
    snake.x = canvas.width - grid;
  }
  else if (snake.x >= canvas.width) {
    snake.x = 0;
  }
  
  // wrap snake position vertically on edge of screen
  if (snake.y < 0) {
    snake.y = canvas.height - grid;
  }
  else if (snake.y >= canvas.height) {
    snake.y = 0;
  }

  // keep track of where snake has been. front of the array is always the head
  snake.cells.unshift({x: snake.x, y: snake.y});

  // remove cells as we move away from them
  if (snake.cells.length > snake.maxCells) {
    //snake.cells.pop();
  }

  // draw apple
  context.fillStyle = 'gold';
  context.fillRect(apple.x, apple.y, grid-1, grid-1);

  // draw snake one cell at a time
  context.fillStyle = 'white';
  snake.cells.forEach(function(cell, index) {
    
    // drawing 1 px smaller than the grid creates a grid effect in the snake body so you can see how long it is
    context.fillRect(cell.x, cell.y, grid-1, grid-1);  

    // snake ate apple
    if (cell.x === apple.x && cell.y === apple.y) {
      snake.maxCells++;
      num.innerHTML = Number(num.innerHTML) + 1;


      // canvas is 400x400 which is 25x25 grids 
      apple.x = getRandomInt(0, 25) * grid;
      apple.y = getRandomInt(0, 25) * grid;
    }

    // check collision with all cells after this one (modified bubble sort)
    for (var i = index + 1; i < snake.cells.length; i++) {
      
      // snake occupies same space as a body part. reset game
      if (cell.x === snake.cells[i].x && cell.y === snake.cells[i].y) {
        snake.x = 0;
        snake.y = 0;
        snake.cells = [];
        snake.maxCells = 4;
        snake.dx = grid;
        snake.dy = 0;

        apple.x = getRandomInt(0, 25) * grid;
        apple.y = getRandomInt(0, 25) * grid;
        num.innerHTML = 0;
      }
    }
  });
}

// listen to keyboard events to move the snake
document.addEventListener('keydown', function(e) {
  // prevent snake from backtracking on itself by checking that it's 
  // not already moving on the same axis (pressing left while moving
  // left won't do anything, and pressing right while moving left
  // shouldn't let you collide with your own body)
  
  // left arrow key
  if (e.which === 37 && snake.dx === 0) {
    snake.dx = -grid;
    snake.dy = 0;
  }
  // up arrow key
  else if (e.which === 38 && snake.dy === 0) {
    snake.dy = -grid;
    snake.dx = 0;
  }
  // right arrow key
  else if (e.which === 39 && snake.dx === 0) {
    snake.dx = grid;
    snake.dy = 0;
  }
  // down arrow key
  else if (e.which === 40 && snake.dy === 0) {
    snake.dy = grid;
    snake.dx = 0;
  }
});

// start the game
requestAnimationFrame(loop);
</script>
</body>
</html>
</html>

