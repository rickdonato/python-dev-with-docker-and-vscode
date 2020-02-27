# Python Development with Docker and VSCode

There are 2 methods you can use to run the application inside a container-based development environment.
For this you will to have Docker installed, and if you want to follow the VS Code method you will Visual Studio Code and its extensions. See pre-requisites.

## Standalone Container

You can build the `Dockerfile.standalone` image which will use the `continuumio/miniconda3` image, copy the projects files to `/app` directory in the container, with the execption of the paths indicated in the `.dockerignore` file, and install the project python dependencies.

### Procedure

Clone repository.

```shell
> git clone git@bitbucket.org:packetflow/python-development-with-docker-and-vscode.git
```

Build Docker image.

```shell
> cd python-development-with-docker-and-vscode
> docker build -t example/intro-netautomation:latest -f Dockerfile.standalone .
```

This will use the contents of `Dockerfile.standalone` to create the image. Don't forget the `.` at the end of the command!

Spin up and connect to container.

```shell
> docker run -it --name example01 example/intro-netautomation:latest
```

This will run and login into the container. You now have access to python, conda and project files under the `/app` directory.

**NOTE**: Work done on the container WILL be erased when you DELETE the container, but you don't have to worry to STOP the container - changes will still be there. That is why is highly recommended to use *git* or another SCM system to work with this type of project.

## VS Code Based Container

### Pre-Requisites

* Have [Remote-Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) installed.
* And also recommended the [Docker extension](https://code.visualstudio.com/docs/azure/docker#_install-the-docker-extension) for managing the containers.

### Procedure

Using the [Visual Studio Code Editor](https://code.visualstudio.com/) you can automatically setup the docker development environment. You just have to do the following

Clone the repository.

```shell
> git clone git@bitbucket.org:packetflow/python-development-with-docker-and-vscode.git
```

Open a new VS Code window and select **Remote-Containers: Open in a container**, and select the directory where the project was cloned.

This will launch a new window where it will show output of VS Code building the image with the specifications dictated on `Dockerfile` and the instructions on the `.devcontainer/devcontainer.json`.

By then you should have a fully functional development environment for this project.
