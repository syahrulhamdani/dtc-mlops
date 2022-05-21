# Week 1 - Introduction

This directory contains all attempts (code, files, config, etc.) and notes for week 1 of the bootcamp.


## Environment Preparation

I use Google Cloud Platform instead of AWS. If you worry about the price, just create a new google account and apply for the GCP free tier.

The steps taken for GCP:
* make sure you can access your cloud console and create a project already
* go to Compute Engine and create a new instance (enable the API first if you haven't). The VM config I used:
	* name: `mlops-zoomcamp`
	* region: `us-west1`, zone: `us-west1-b`
	* machine: `N2`, type: `n2-standard-2`
	* boot disk image: `Ubuntu 22.04 LTS`
	* firewall: allow both HTTP and HTTPS traffic
* before you press `Create`, configure your SSH keys
	* follow this [docs](https://cloud.google.com/compute/docs/connect/create-ssh-keys) to create SSH keys based on your local OS
	* copy your public ssh key file (the one `.pub` extension) to clipboard
	* on GCP, go to Security section, and add your SSH keys at "Add manually generated SSH keys" section
* press `Create` button and wait your instance to be created

To access the VM through your local terminal, just follow the original video.


## Using [pyenv](https://github.com/pyenv/pyenv) instead of Anaconda

I prefer pyenv and pipenv for managing python version and virtual environment. Anaconda is just to heavy and not reliable for me, personally.
Hence, I didn't install Anaconda on the VM, I install pyenv.

If you want it, you can follow these steps:
* if you love being hardcore, follow the installation steps with git in the official [docs](https://github.com/pyenv/pyenv#basic-github-checkout)
* if you want fast installation, use [pyenv-installer](https://github.com/pyenv/pyenv-installer)
* after that, continue to follow the instructions in pyenv official installation guide for [shell environment](https://github.com/pyenv/pyenv#set-up-your-shell-environment-for-pyenv)
* don't forget to `source` your `.profile` file (or `.bash_profile`, `.zshrc`, etc.)

Before installing specific python version, first you need to install some python dependencies.
Just follow this [wiki](https://github.com/pyenv/pyenv/wiki#suggested-build-environment) and look for Ubuntu suggested build.

For this bootcamp, I use **Python 3.9.12** (no specific reason). The command used to install that version with pyenv:

```bash
pyenv install 3.9.12
```

If you want other versions, you can look at the available list by using command:

```bash
pyenv install --list
```

> You can even install more than one python version using pyenv.

Last command to use the python version is to make it as global python version. Use:

```bash
pyenv global 3.9.12
```

For sanity check, type `python` and you should be entering Python 3.9.12 interface. Or, you can use command `pyenv which python`.
To check the list of python versions you already installed, just run `pyenv versions`.


## Using pyenv-virtualenv

To create a virtual environment using pyenv, just type

```bash
pyenv virtualenv [version] [env_name]
```

For example, if I want to create a virtual environment using Python 3.9.7 and name it as `mlops-zoomcamp`, I just type:

```bash
pyenv virtualenv 3.9.7 mlops-zoomcamp
```

To activate it, I suggest you don't. You can use it directly in you desired workspace by attach it as local environment.
For example, if you want to use the environment in mlops-zoomcamp directory, just `cd` inside it, and run command below:

```bash
pyenv local mlops-zoomcamp
```

Every time you enter the directory, the virtual environment will be activated automatically.
