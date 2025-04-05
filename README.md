<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Play your favorite unblocked games online">
    <title>GameHub - Play Unblocked Games Online</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary-color: #ff6b00;
            --primary-hover: #e05e00;
            --background-dark: #1a1a1a;
            --background-light: #2d2d2d;
            --text-color: #ffffff;
            --text-secondary: #cccccc;
            --transition-speed: 0.3s;
        }
        
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }
        
        body {
            font-family: 'Poppins', Arial, sans-serif;
            background-color: var(--background-dark);
            color: var(--text-color);
            line-height: 1.6;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
        }
        
        header {
            background: linear-gradient(135deg, #333 0%, #111 100%);
            padding: 1.5rem;
            text-align: center;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.3);
        }
        
        h1 {
            font-size: 2.2rem;
            font-weight: 700;
            background: linear-gradient(to right, #ff8a00, #ff4d00);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            margin-bottom: 0.5rem;
        }
        
        .subtitle {
            color: var(--text-secondary);
            font-size: 1rem;
            font-weight: 400;
        }
        
        .game-container {
            max-width: 1200px;
            width: 90%;
            margin: 2rem auto;
            flex: 1;
        }
        
        .game-menu {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 1rem;
            margin-bottom: 2rem;
        }
        
        button {
            background-color: var(--primary-color);
            color: white;
            border: none;
            padding: 0.8rem 1.5rem;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            border-radius: 8px;
            transition: all var(--transition-speed) ease;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            min-width: 120px;
        }
        
        button:hover, button:focus {
            background-color: var(--primary-hover);
            transform: translateY(-2px);
            box-shadow: 0 6px 8px rgba(0, 0, 0, 0.15);
        }
        
        button:active {
            transform: translateY(0);
        }
        
        .game-display {
            background-color: var(--background-light);
            border-radius: 12px;
            padding: 1.5rem;
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
        }
        
        h2 {
            margin-bottom: 1rem;
            color: var(--text-color);
        }
        
        iframe {
            width: 100%;
            height: 600px;
            border: none;
            border-radius: 8px;
            background-color: #000;
            transition: opacity var(--transition-speed) ease;
            box-shadow: inset 0 0 20px rgba(0, 0, 0, 0.5);
        }
        
        #loading {
            display: none;
            font-size: 1.2rem;
            color: var(--primary-color);
            margin: 1rem 0;
            text-align: center;
        }
        
        .spinner {
            border: 4px solid rgba(255, 107, 0, 0.3);
            border-radius: 50%;
            border-top: 4px solid var(--primary-color);
            width: 30px;
            height: 30px;
            animation: spin 1s linear infinite;
            margin: 0 auto 1rem;
        }
        
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        
        footer {
            background-color: var(--background-light);
            text-align: center;
            padding: 1rem;
            margin-top: auto;
            font-size: 0.9rem;
            color: var(--text-secondary);
        }
        
        @media (max-width: 768px) {
            h1 {
                font-size: 1.8rem;
            }
            
            .game-menu {
                flex-direction: column;
                align-items: center;
            }
            
            button {
                width: 100%;
                max-width: 250px;
            }
            
            iframe {
                height: 400px;
            }
        }
        
        @media (max-width: 480px) {
            iframe {
                height: 300px;
            }
        }
        
        /* Accessibility focus styles */
        button:focus, a:focus {
            outline: 3px solid #ff8a00;
            outline-offset: 2px;
        }
    </style>
</head>
<body>
    <header>
        <h1>GameHub</h1>
        <p class="subtitle">Your portal to unblocked gaming fun</p>
    </header>
    
    <main class="game-container">
        <div class="game-menu" role="navigation" aria-label="Game selection">
            <button onclick="loadGame('Super Adventure', '/proxy?url=game1-url')" aria-label="Play Super Adventure">
                Super Adventure
            </button>
            <button onclick="loadGame('Space Explorer', '/proxy?url=game2-url')" aria-label="Play Space Explorer">
                Space Explorer
            </button>
            <button onclick="loadGame('Racing Challenge', '/proxy?url=game3-url')" aria-label="Play Racing Challenge">
                Racing Challenge
            </button>
            <button onclick="loadGame('Puzzle Master', '/proxy?url=game4-url')" aria-label="Play Puzzle Master">
                Puzzle Master
            </button>
        </div>
        
        <div class="game-display">
            <h2 id="gameTitle">Select a game from the menu above</h2>
            <div id="loading">
                <div class="spinner" aria-hidden="true"></div>
                <p>Loading game, please wait...</p>
            </div>
            <iframe 
                id="gameFrame" 
                src="about:blank" 
                onload="hideLoadingIndicator()"
                title="Game display"
                allow="fullscreen"
                aria-label="Game content"
                sandbox="allow-scripts allow-same-origin allow-forms allow-popups allow-pointer-lock"
            ></iframe>
        </div>
    </main>
    
    <footer>
        <p>&copy; 2023 GameHub. All games are property of their respective owners.</p>
    </footer>
    
    <script>
        // Cache DOM elements for better performance
        const gameFrame = document.getElementById('gameFrame');
        const loadingIndicator = document.getElementById('loading');
        const gameTitle = document.getElementById('gameTitle');
        
        function loadGame(gameName, url) {
            try {
                // Show loading indicator
                loadingIndicator.style.display = 'block';
                gameFrame.style.opacity = '0';
                gameTitle.textContent = `Now Playing: ${gameName}`;
                
                // Clear previous game
                gameFrame.src = 'about:blank';
                
                // Small delay to allow UI to update before heavy load
                setTimeout(() => {
                    gameFrame.src = url;
                }, 100);
                
                // Track game selection (could be used for analytics)
                console.log(`Game selected: ${gameName}`);
            } catch (error) {
                console.error('Error loading game:', error);
                loadingIndicator.style.display = 'none';
                gameTitle.textContent = 'Error loading game. Please try again.';
            }
        }

        function hideLoadingIndicator() {
            loadingIndicator.style.display = 'none';
            gameFrame.style.opacity = '1';
            
            // Focus the iframe for keyboard controls
            gameFrame.focus();
        }
        
        // Keyboard navigation for game buttons
        document.addEventListener('DOMContentLoaded', () => {
            const buttons = document.querySelectorAll('.game-menu button');
            
            buttons.forEach((button, index) => {
                button.addEventListener('keydown', (e) => {
                    if (e.key === 'ArrowRight' && index < buttons.length - 1) {
                        buttons[index + 1].focus();
                    } else if (e.key === 'ArrowLeft' && index > 0) {
                        buttons[index - 1].focus();
                    }
                });
            });
        });
    </script>
</body>
</html>S
