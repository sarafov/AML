# Applied Machine Learning (INFR11211)
This repository contains the Python files for the AML labs. It also contains instructions for how to get started. We recommend that you use Noteable to do the labs. 

## Gettting Started: Using [Noteable](https://noteable.edina.ac.uk/login)

#### Step 1: 
Go to [Noteable](https://noteable.edina.ac.uk/login). It might ask your UUN and Password, if you are not logged into Euclid. After login, the following screen will be available with few options to start the server. 
<br/>
<img src="assets/step_0.png" width="500" height="200">

#### Step 2: 
Choose *Standard Notebook (Python3)* and click *Start*.
<br/>
<img src="assets/step_1.png" width="500" height="200">

#### Step 2: 
The jupyter notebook will open in the same window, as shown below. On the Noteable home folder, click on the <span style="color:red">*+GitRepo*</span> button.
<br/>
<img src="assets/step_2.png" width="500" height="200">

#### Step 3: 
In the Notebook server, a small pop-up window appears, as shown below:
<br/>
<img src="assets/step_3.png" width="500" height="200">

#### Step 4: 
Go to AML gitlab repo: [aml-labs](https://git.ecdf.ed.ac.uk/aml/labs-public.git) and copy the *HTTPS* link by clicking on the blue colored <span style="color:blue">*Clone*</span> button.
<br/>
<img src="assets/step_4.png" width="500" height="200">

#### Step 5: 
Enter the copied GitLab link in the pop-up window on the Notebook server. Also enter your username (i.e. student number with "s") and the corresponding password. You can leave the Branch textfield blank. Now click *Clone* to copy the labs into Noteable.
<br/>
<img src="assets/step_5.png" width="500" height="200">

#### Step 6: 
Noteable will take few seconds to copy and load the AML Labs.
<br/>
<img src="assets/step_6.png" width="500" height="200">

#### Step 7: 
Once the Noteable is successfull, it will show the repository contents.
<br/>
<img src="assets/step_7.png" width="500" height="200">

#### Step 8: 
Go to `Labs` to find the available jupyter notebook and continue working on them.
<br/>
<img src="assets/step_8.png" width="500" height="200">


## Alternatives to Noteable

The following instructions tell you how to setup Python and how to configure it for the AML labs. If you successfully got Notable working you can skip this step. In this section we provide alternative ways in which you can run the labs - either on DICE or your own computer. The main steps are (i) installing Python (using conda), (ii) configuring the correct libraries required for AML, and (iii) downloading the labs. 

These instructions are primarily written for DICE. 
DICE refers to desktops and servers that run Unix and are managed by computing staff in the School of Informatics. It includes computers that are both physically in the labs and ones that you can access remotely. 


In the instructions below, any text styled `like this` should be executed in
the terminal. You should enter these commands **by hand,
one-by-one**. This is to help detect any issues.
Please read and heed any warnings *and especially errors* you may encounter. We
are on standby in the labs to help if required.



### 0. Using DICE or your own machine
For this course, you can either use (i) **a DICE computer** via remote access or (ii) **your own personal computer** running Linux, Windows, or MacOS. We have verified that these instructions work under DICE and while they should work on your machine too, we can not guarantee this for everyone. If you are using your own computer, you can skip to step 2. 

If you choose to work on DICE, there are two main ways of using it remotely -- either via RDP (remote desktop) or via SSH. The first one is recommended, as it is the easiest. If you are running Linux, run the following command from your own computer:

```
xfreerdp +glyph-cache /relax-order-checks /u:s1234567 /v:s1234567.remote.inf.ed.ac.uk
```

Replace `s1234567` with your username. This will open a remote DICE session and ask you to login. Then you can proceed with the setup instructions below. Guides for remote access using other operating systems can be found here: [http://computing.help.inf.ed.ac.uk/remote-desktop](http://computing.help.inf.ed.ac.uk/remote-desktop).

*If you have used SSH before/know what you are doing*, you can also use the university SSH gateways. The guide is here: [http://computing.help.inf.ed.ac.uk/external-login](http://computing.help.inf.ed.ac.uk/external-login). Note, that you will need to setup port forwarding to be able to access Jupyter notebooks.

#### Accesing the terminal on DICE
If you're on a DICE machine, in the top left click Applications -> Utilities -> Terminal. 
Alternatively, you may find the terminal under Applications -> System Tools -> MATE Terminal, depending on the system used.  

### 1. Check your available space
Note that your space on DICE is allocated dynamically. If you are
having problems it may be because you were using new space faster than it could
be allocated to you!


All DICE users **registered** for AML will automatically be allocated **20GB**
extra space over their default space values. **Please register for the course
ASAP to get this space**.
1. Check how much space you have on DICE. **You will need at least 4.5GB**.
    1. `freespace`
    1. If you don't have enough space, follow the instructions on [this page](
        http://computing.help.inf.ed.ac.uk/afs-quotas).

### 2. If you don't have it - install conda
1. **Check you don't already have conda installed!**
    1. `which conda`
    1. **if you already have it installed, skip ahead to Create an Environment**
    1. It doesn't matter if you have miniconda3, or anaconda3 installed (it does not even matter if it is version 2).
1. If you don't have conda, download the latest version of miniconda3
    1. `cd ~/Downloads` (you can make a Downloads folder if you don't have one)
    1. Download the installer (we prefer to use miniconda since it carries less baggage), depending on your system (you can check links [here](https://conda.io/miniconda.html)):
        * Linux: `wget https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh`
        * Mac: `wget https://repo.continuum.io/miniconda/Miniconda3-latest-MacOSX-x86_64.sh` or ```curl -LOk https://repo.continuum.io/miniconda/Miniconda3-latest-MacOSX-x86_64.sh```
        * Or just simply download from [the site](https://conda.io/miniconda.html)
1. Install miniconda3 *with default settings*
    1. `bash Miniconda3-latest-Linux-x86_64.sh`
    1. Follow the prompt - **type `yes` and hit `enter` to accept all default
    settings when asked**
1. Close Terminal and reopen
1. Try executing `conda -h`. If it works, you can delete the installer ```rm ~/Downloads/Miniconda3-latest-Linux-x86_64.sh```

If you are installing conda on your own machine, you will find some instructions for Windows users at the end of this README.

### 3. Create an environment for AML
1. Update conda: `conda update conda`
1. Create the environment for the course. Call it py3aml and install python 3 (*hence the name*):
```conda create -n py3aml python=3.9.2```

You can find more information in the Miscellaneous section below for how to work with conda environments. Briefly, `source activate py3aml` will activate the new environment and `conda deactivate` will exit it. 

### 4. Get the course lab material

Before installing required modules, we need to obtain the repository since it includes the specifications of the packages to use (as well as all lab material). Within your terminal:

1. Navigate back to your home directory: `cd`
1. Now you have two options:
    1. If **and only if** you are familiar and confident with using Git/GitHub, you can initialize a git directory, add the above repo as remote and pull everything into your local directory, something like:
        * `git clone https://git.ecdf.ed.ac.uk/aml/labs-public.git
    1. **OTHERWISE**, we recommend that you directly download a .zip file from [https://git.ecdf.ed.ac.uk/aml/labs-public](https://git.ecdf.ed.ac.uk/aml/labs-public) which will contain everything you need and save it in the folder you have just created (by clicking the Download icon -> zip).
1. Navigate to the new directory
    * `cd labs-public`

#### *IMPORTANT*
Supporting and teaching git is not in scope for this course so please only use it if you are happy to google your own solutions! That being said, git is a better alternative if you are familiar with it. We reccommend that you work with your own branch/fork as the git repository is read-only.

### 5. Install all the packages for AML
1. Activate the environment: ```source activate py3aml```
1. {May take 5 minutes} Install all required packages. We have done a *aml.req* file for you to use: ```conda install --file aml.req```. You can download this as part of the repository (see below).
   **It is important to use this requirements file as this contains the specific version numbers so that the course is consistent regardless of when you start**
1. If the packages are listed as not being available you can try adding conda forge to your list of channels: ```conda config --append channels conda-forge```
1. Get some space back: ```conda clean -a```

#### *IMPORTANT*
Before starting any AML work in a new terminal **you must always activate the aml conda environment** using `source activate py3aml`. If the environment is not activated, you will be using your base python with its own set of packages. If you are ever in any doubt of which python version is being used, execute `which python` and make sure that it points to where your environments are installed.

### 6. Starting a Notebook
Once you have downloaded the material, you are now ready to start working with
Jupyter notebooks. First you need to activate the software environment and then
start a Jupyter Notebook session from within the folder where the material is
stored. *You will have to follow this procedure for all labs and assignments.*

1. Activate the conda environment: `source activate py3aml`
2. Enter the directory where you downloaded the course material:
`cd labs-public`
3. Start a jupyter notebook
    * `jupyter notebook`
4. This should automatically open your browser
    * Click on `00 - Introduction.ipynb ` to open it (it exists under the Labs directory)

Now you are ready to start working on the labs!

### Further Reading

- Conda getting started - 30 minute practical well worth going through [https://conda.io/docs/user-guide/getting-started.html](https://conda.io/docs/user-guide/getting-started.html)
- System Environment variables - [https://en.wikipedia.org/wiki/Environment_variable](https://en.wikipedia.org/wiki/Environment_variable)
- Linux execution order - [https://www.cyberciti.biz/tips/how-linux-or-unix-understand-which-program-to-run-part-i.html](https://www.cyberciti.biz/tips/how-linux-or-unix-understand-which-program-to-run-part-i.html)

### Troubleshooting

#### I ran out of space when installing packages

Firstly, please note that your space on DICE is allocated dynamically. If you are
having problems it may be because you were using new space faster than it could
be allocated to you!
1. Check how much space you have on DICE. **You will need at least 4.5GB**.
    1. `freespace`
    1. If you don't have enough space, follow the instructions on [this page](
        http://computing.help.inf.ed.ac.uk/afs-quotas)
1. Try installing packages individually and executing `conda clean --all` after
each installation

#### Deleting an environment
If you install incorrect packages, or a package breaks for some reason, you can
just delete your environment and start again. Execute `conda remove --name py3aml
--all` then install the package as described above.

#### Deleting your entire conda installation
This is fairly extreme but as a final resort can be done quickly and easily.
Please note that you will lose *all* your environments if you do this, so check
this will not affect you before proceeding...[follow instructions here](https://conda.io/docs/user-guide/install/linux.html?highlight=uninstall#uninstalling-anaconda-or-miniconda)

#### conda: command not found or 'Conda never works in new terminal'
DICE issue: DICE has a different set of bash startup mechanism, and you may need
to edit some different files yourself. **Do the below with ~/.benv instead**. See [here](http://computing.help.inf.ed.ac.uk/dice-bash) for more info.

Unix solution: First try closing your terminal and reopening. If that doesn't fix, it's likely that, in the conda installation, you didn't allow conda to add the it's bin directory to your $PATH. Check your home directory for `~/.brc` or `~/.bashrc`. You should have a line in one of those files that looks like this (the XX's represent your student number):
```
export PATH="$PATH:/afs/inf.ed.ac.uk/user/sXX/sXXXXXXX/miniconda3/bin"
```
If it does not exist, simply add it. *Note: it does not normally matter if the PATH is prepended or appended, but I prefer to append.*
You will then need to activate this change. You can either exit the terminal and reopen a new one, or simply source it:
```
source ~/.brc
```

#### 'source' is not recognized as an internal or external command, ...
You're on windows aren't you! Please see the note at the top of the file (replace `source` with `conda`)

#### 'which' is not recognized as an internal or external command, ...
You're on windows aren't you! Please see the note at the top of the file (`which` = `where` on windows).

#### $PATH?
You're on windows aren't you! Please see the note at the top of the file (`echo $PATH` == `echo %PATH%` on windows).

#### I can't find my conda environment....but I definitely created it
We have found that people also taking MLP and/or ANLP (other courses that use
conda) have installed multiple versions of conda. To check whether you've done
this, simply list your home directory:

```{bash}
ls ~
```

If you see multiple folders called anaconda or miniconda, e.g. anaconda3 and
miniconda2, you have installed multiple versions of conda! Another way to check
is to print your PATH or view your .brc / .benv:

```
echo $PATH
cat ~/.brc
cat ~/.benv  # if you're on DICE
```

This will show multiple conda directories.

You only need to use one installation of conda, and it doens't matter whether
you use version 2 or 3 (there is no difference that will affect this course).

Simply recreate your environment(s) in one of the conda installations, and
delete the other.

- https://conda.io/docs/user-guide/tasks/manage-environments.html#sharing-an-environment
- https://conda.io/docs/user-guide/install/linux.html#uninstalling-anaconda-or-miniconda


### Miscellaneous

### What is an environment?
An environment is a collection of packages of specific versions. You can have
multiple environments and switch between them for different projects. Conda is
a tool for managing both environments *and* the packages within each
environment. Here is a quick introduction:

1. Show a list of your environments: `conda env list`
1. Print `$PATH`, one of your system's [environment variables](https://en.wikipedia.org/wiki/Environment_variable), in the
terminal: `echo $PATH`
    * `$PATH` is the list of directories your terminal can search to find
anything you execute:
1. Print a list of python installations on your `$PATH` (the top one is the one
    that will get executed if you type `python` in the terminal):
    `which python -a`
1. Activate the new environment: `source activate py3aml`
1. Show list of python installations on your system *now*: `which python -a`
1. Show your system `$PATH` again: `echo $PATH`
1. Deactivate the new environment: `source deactivate`
1. Observer how your $PATH has changed again: `echo $PATH`
1. Make an empty environment: `conda create --name empty`
1. You can clone environments; this is useful for backing up: `conda create
--name empty_bkp --clone empty`
1. Make another python 3 environment with numpy already installed: `conda create
--name py3 python=3 numpy`
1. `conda env list`
1. Activate py3: `source activate py3`
1. Show the installed packages: `conda list`
1. Switch environments: `source deactivate; source activate empty`
1. `conda list` to show packages (note that python and, crucially,
    [pip](https://pip.pypa.io/en/stable/) are not installed)
1. Q: What python would get used now? `which python` A: the conda root
environment installation of python i.e. *not* this environment's python.
1. Install numpy: `conda install numpy`
1. Q: What python would get used *now*? `which python` A: You may have clocked
that conda installed a dependency of numpy (a python package)...python!
1. Let's delete these test environments:
    * `source deactivate`
    * `conda env list`
    * `conda remove --name empty --all`
    * `conda remove --name empty_bkp --all`
    * `conda remove --name py3 --all`
    * `conda env list`

### Windows users
* After conda installation, all instructions are much the same
* Please follow conda installation instructions on their
website [here](https://docs.conda.io/projects/conda/en/latest/user-guide/install/windows.html)
* To activate the `py3aml` environment, note that you don't type `source activate py3aml`
but instead use `conda activate py3aml`
* You can ignore "What is an environment?" (though you can google windows equivalents of all
  the Unix commands given)
