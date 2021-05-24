### This is basic docker file to run the python program on linux machine 
__we assume  current user have sudo permission__
>Step 1: Creating the Python Script

Create a simple Python Script with called even_odd.py inside a directory.
 Copy the below statement inside the Python script and save it inside the directory.
 
 ```.env
n = int(input("Enter the number").strip())

num = n%2

if num == 0:
    print("The Number is Even")
else:
    print("The number is ODD")
```

>Step 2: Creating the Dockerfile

Inside the same directory, create another file called Docker file. In this file, we will define the sequence of steps needed to create the Docker Image. 
Take a look at the below Dockerfile template.

```.env
FROM python:3.8
WORKDIR /usr/src/app
COPY . .
CMD ["even_odd.py"]
ENTRYPOINT ["python3"]
```

In the above Dockerfile, we have pulled the Python 3.8 Base Image from the Docker Repository. 
We have set the working directory to /usr/src/app. After that, we have copied all the files to the 
working directory. Using CMD and ENTRYPOINT instructions, 
we have instructed the Container to run the even_odd.py Python script when the container is started.

>Step 3: Building the Docker Container

After you have created both the Python script and the Dockerfile,
you can now use the Docker build command to build your Docker Image.

```.env
sudo docker build -t even_odd .
```

>Step 4: Verify the Image Build

After you have built your Docker Image,
you can list all the Images to check whether your image has been successfully built or not.

```shell script
docker images 
```

You will find your Image name listed here.

>Step 5: Running the Docker Container

Now, you can use the Docker run command to run your Docker Container.

```shell script
docker run -it even_odd
```

After running the Docker Container,
it will ask to enter the number  
after user input the number 
you will see the output number is even or odd  printed inside the bash.