# JarvisAI

## List of steps to configure Jarvis and HuggingGPT locally. Use along with video explanation: https://www.youtube.com/watch?v=sJY70H4deV0

![Intro image v1](https://github.com/pablocity/JarvisAI/assets/23730106/37ad1a84-6ea5-476f-8bbf-6d4b87e3136e)

```
wsl --install

git clone https://github.com/microsoft/JARVIS.git

// Anaconda repo
https://repo.anaconda.com/archive/

// Download Anaconda installer script
wget https://repo.anaconda.com/archive/Anaconda3-2023.03-1-Linux-x86_64.sh

// change permission of this script to executable
chmod +x Anaconda3-2023.03-1-Linux-x86_64.sh

./Anaconda3-2023.03-1-Linux-x86_64.sh

// create virtual environment
conda create -n jarvis python=3.8

//activate virtual environment
conda activate jarvis

conda install pytorch torchvision torchaudio pytorch-cuda=11.7 -c pytorch -c nvidia

pip install -r requirements.txt

sudo apt update

sudo apt install build-essential

// get repository for installing git-lfs
curl -s https://packagecloud.io/install/repositories/github/git-lfs/script.deb.sh | sudo bash

sudo apt install git-lfs

// download machine learning models (run in JARVIS/server/models)
bash download.sh

/* open config file in visual studio code if its in your path, if not use for example nano. It is also possible to access ubuntu file system in windows (when using wsl) - in file explorer enter: \\wsl$ and you can now navigate to config file and open in any editor on windows
*/

// in JARVIS/server/configs
code config.default.yaml OR nano config.default.yaml

// openAI api key
https://platform.openai.com/account/api-keys

// hugging face token
https://huggingface.co/settings/tokens

// check ip address
ip addr


//running jarvis - if any of those two actions will result in message "Killed" in console its propable that you don't have enough resources to run jarvis in mode specified in config file - change it then to minimal and check if it works

python models_server.py --config configs/config.default.yaml
python awesome_chat.py --config configs/config.default.yaml --mode server

// web application configuration

// if you have installed nodejs or npm in windows do these steps to avoid conflicts when installing dependencies

1. sudo nano /etc/wsl.conf
2. append to this file following lines:
   [interop]
   appendWindowsPath = false
3. restart Ubuntu

// installing nvm
curl https://raw.githubusercontent.com/creationix/nvm/master/install.sh | bash

// restart ubuntu

nvm install 16
nvm use 16

// go to JARVIS/web/src/config
nano index.ts

// change HUGGINGGPT_BASE_URL to ip address obtained using ip addr command

// run web application (first you need to run previous commands to start the server)
'python models_server.py --config configs/config.default.yaml
 python awesome_chat.py --config configs/config.default.yaml --mode server'
 
// from JARVIS/web

npm install
npm run dev

Enjoy!

```
