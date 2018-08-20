# asksteem-bot
The source code of the AskSteem bot.

# run docker directly with simple app
docker run -it --rm \
  -v "$PWD":/usr/src/app \
  -w /usr/src/app \
  python:3-alpine python related_posts.py
  
docker run -it --rm \
  -v "$PWD":/usr/src/app \
  -w /usr/src/app \
  python:2-alpine python related_posts.py
  

# build docker image using Dockerfile 
FROM python:3-alpine

WORKDIR /usr/src/app

RUN apk add no-cache git bash nano 
COPY requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

CMD [ "python", "./your-daemon-or-script.py" ]

