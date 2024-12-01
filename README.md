
# PieRat
Yet another RAT for administrating multiple clients connected to a telegram bot. 

```I decided to make this project public as I have lost the motivation to sell this. In order to prevent 'skids' from using this tool, I will not provide installation support. For the sake of this project, I will not give a tutorial on how to setup Redis Cloud.```

```I am not responsible for any damages inflicted by this tool, this tool was made for educational intent as a side project, I do not condone any malicious activity with this tool.```
## Features

### General

- Upload / Download : Download and Upload files from/to Telegram.
- Shell : Run shell commands.
- Screenshot: Screenshot and send to user.
- File management: Manage files on clients e.g cd, pwd, ls, move, copy, delete, mkdir.
- Process Management: Be able to view and kill processes on demand.
- Show system info


### Fun

- Message Box: Show message box to target computer.
- Jumpscare: Play loud and frightening videos on target computer.
- Volume Management: Set and Get Volume.
- Audio Player: Start and Play audio from audio file on target.
- TTS: Play Text To Speech on target computer.
- Open URL: Open a url in default browser.

### Other
- Keylogger: Start and Stop Keylogging.
- Proxy: Start and Stop Proxy, host with ngrok.
- DNS Poisoner (block any site and AV sites)

### Modules (auto installable)

#### Camera
- List Cameras.
- Snap Camera.

## Installation


### Prerequisites
- Redis Server
- Telegram bot token and Chat ID


First clone this repo and travese into it.

```bash
git clone https://github.com/python312/pierat.git 
```
```bash
cd pierat
```

Create enviorment and install requirments.

```
python -m venv pierat
```

```
.\pierat\Scripts\activate.bat
```


```bash
pip install -r requirements.txt
```

Edit the ```main.py``` and ```populator.py``` scripts and fill out with your configuration.
## How it works.

The system operates with the ```populator.py``` script, which serves as the single poller to fetch Telegram updates and populate them into the Redis server. This approach addresses the limitation of a single bot instance being allowed to poll updates by centralizing the process through ```populator.py```. This script is only required to run while interacting with the bot. Worker processes, referred to as "zombies," connect to the Redis server to retrieve and process updates, reducing load and bypassing polling restrictions. Zombies handle tasks based on their assigned roles, reacting to updates accordingly. The Redis server also manages the assignment of specific computers by comparing their UUIDs with preconfigured values that are set in the Redis. Additionally, ```populator.py``` processes global commands, such as ```/list_computers``` and ```/set_computer```
## Usage

1. Compile ```main.py``` with your favourite compiler, e.g ```pyinstaller``` ```nuitka```
2. Run ```populator.py``` in the background
3. Deploy the main.py executable.
## Acknowledgements

- ChatGPT, helped me in some of the minor things / bugs.
