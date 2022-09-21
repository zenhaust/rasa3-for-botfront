### Before GO !!!
This rasa fork can not run in standalone mode.<br>
It's a part of [botfront-for-rasa3](https://github.com/djypanda/botfront-for-rasa3) project.<br>
It requests configurations from botfront-for-rasa3 backend service. And also use botfront backend service as a response and track server.

### Run in docker

1. Get the sourcecode
```bash
git clone https://github.com/djypanda/rasa3-for-botfront.git
cd rasa3-for-botfront
```
2. Build the docker image
If you run into some build errors due to the network connection problem (especially in cn), just run this command again.
```bash
docker build -t rasa3-for-bf:v0.1 -f docker/Dockerfile.botfront .
```
3. Check the image
```bash
docker images
```
You should get a output like this:
```
REPOSITORY             TAG       IMAGE ID       CREATED          SIZE
rasa3-for-bf           v0.1      3e604ad10384   43 seconds ago   2.33GB
```

Now rasa docker image is ready, go to [botfront part](https://github.com/djypanda/botfront-for-rasa3) for the next step;

### Development Installation

1. Download sourcecode and create virtual environment:
```bash
git clone https://github.com/djypanda/rasa3-for-botfront.git
cd rasa3-for-botfront
python3 -m venv ./venv
source ./venv/bin/activate
```
2. Install poetry:
```bash
curl -sSL https://install.python-poetry.org | python3 -
```
3. Install rasa:
```bash
poetry install
```
4. Run rasa:
```bash
# Change this project id to the project id created in botfront frontend
export BF_PROJECT_ID=chitchat-9D1ct-aMp
# This URL is for rasa service to get endpoint/credential config from botfront service
export BF_URL=http://localhost:3000/graphql 
rasa run --cors * --debug --enable-api
```

<h2 align="center">
    <a href='https://github.com/RasaHQ/rasa'> Official rasa instruction goes here !!! </a>
</h2>
