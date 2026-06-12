---
title: "setting PATH to use subfolders"
date: 2009-05-14
forum: General Help
---

### Post by silkwj on 2009-05-14
Hi Everyone,

Is there a way (in Ubuntu 9.04), when adding folders to the PATH environment variable in etc/environment, to make it also search all subfolders of the specified folder? I use lots of scripts which reside in project-specific folders all under a master project folder, but i don't want to have to add each project folder to PATH. It doesn't seem to recognize something like: ```
.../folder/*
```Thanks!

---

### Post by capscrew on 2009-05-14
> **silkwj said:**
> Hi Everyone,

Is there a way (in Ubuntu 9.04), when adding folders to the PATH environment variable in etc/environment, to make it also search all subfolders of the specified folder? I use lots of scripts which reside in project-specific folders all under a master project folder, but i don't want to have to add each project folder to PATH. It doesn't seem to recognize something like: ```
.../folder/*
```Thanks!

You should not edit the /etc/environment file. See [**_here_**]("https://help.ubuntu.com/community/EnvironmentVariables") for $PATH information.

---

### Post by silkwj on 2009-05-14
capscrew,

thanks for the advice but i'm still stuck. the page on environmental variables didn't clarify my problem. is there any way, in whatever file i should be editing, to add any and all subfolders to the path for all my project scripts?

---

### Post by capscrew on 2009-05-14
> **silkwj said:**
> capscrew,

thanks for the advice but i'm still stuck. the page on environmental variables didn't clarify my problem. is there any way, in whatever file i should be editing, to add any and all subfolders to the path for all my project scripts?

There is nothing that I am aware of in the *Linux kernel* that addresses your situation directly.   If there is anything it would be a script of some sort...and that's how *nix tools come about.

---

### Post by spiderbatdad on 2009-05-14
in /home/<user>/.bashrc like so:
```
export PATH=$PATH:$HOME/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$Home/bin
```where bin is the project folder.
```
$PATH
```To see directories in PATH

---

