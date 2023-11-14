# WebApp Dockerised

We need to first make a virtual environment for our application in our system

```bash
python3 -m venv venv
. venv/bin/activate
```

This project

```bash
docker pull w3ts0ck3t/devops_project
```

Now we will create our requirements file in project root using

```bash
pip freeze > requirements.txt
```

Let's create our Dockerfile

```Dockerfile
FROM python:3.8

WORKDIR /fastapi-app

COPY requirements.txt .

RUN pip install -r requirements.txt

COPY ./app ./app

CMD ["python", "./app/main.py"]
```

Build our image on docker

```bash
docker build -t python-fastapi-app .
```

If we want to forward our port

```bash
docker run -p 8000:8000 python-fastapi-app
```

If we want to get the shell inside the container we can get it using

```bash
docker exec -it <container_id/container_name> /bin/sh
```

If we want to push our image to docker hub

```bash
docker tag python-fastapi-app:latest <USERNAME>/<REPO_NAME>:latest
docker push <USERNAME>/<REPO_NAME>:latest
```

After pushing pull the project

```bash
docker pull <USERNAME>/<REPO_NAME>:<TAG>
```
