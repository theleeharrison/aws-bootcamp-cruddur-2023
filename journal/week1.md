# Week 1 — App Containerization
## Homework Submission - @theleeharrison

### Creating the App - Backend and Frontend Containers

Docker wasn't present on my Gitpod environemnt so I went to the extentions tab within VSCode and installed it.

I created a [Dockerfile](https://github.com/theleeharrison/aws-bootcamp-cruddur-2023/blob/main/backend-flask/Dockerfile) within the backend-flask folder. The file contains the code shown below:

```dockerfile
FROM python:3.10-slim-buster

#Inside container
#Creates new folder inside container
WORKDIR /backend-flask


#Outside Container > Inside Container
COPY requirements.txt requirements.txt

#installs python libraries for use in app
RUN pip3 install -r requirements.txt

#Outside Container to Inside Container
# . (period) means everything in current dir
# first period /backend-flask outside container
# second period /backend-flask inside container
COPY . .

#sets env vars
ENV FLASK_ENV=development


EXPOSE ${PORT}

# command to run application within docker container
# python3 -m flask run --host=0.0.0.0 --port=4567 *this was a test to run in local gitpod*
CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0", "--port=4567"]```

