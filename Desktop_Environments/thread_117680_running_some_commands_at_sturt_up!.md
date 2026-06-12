---
title: "running some commands at sturt up!"
date: 2006-01-15
forum: Desktop Environments
---

### Post by hadian on 2006-01-15
i want to run some command as soon as the system boots up. these commands introduce the Intel Fortran and C++ compiler. i added them to .bashrc file, but they will run only in console. i added the to /etc/profile file, but they did not act. also i saved them in a file (a.sh) and added the line source /home/mohammad/a.sh to /etc/profile and again it did not act.
could anybody let me know how to run these commands after booting the sustyem? i want the eclipse to be able to use the compilers. the commands are:
```

# intel fortran
PATH="/opt/intel/fc/9.0/bin:$PATH"
export PATH

LD_LIBRARY_PATH="/opt/intel/fc/9.0/lib:$LD_LIBRARY_PATH"
export LD_LIBRARY_PATH

MANPATH="/opt/intel/fc/9.0/man:${MANPATH}"
export MANPATH

INTEL_LICENSE_FILE="${INTEL_LICENSE_FILE}:/opt/intel/fc/9.0/licenses:/opt/intel/licenses:${HOME}/intel/licenses"
export INTEL_LICENSE_FILE

# intel cpp
PATH="/opt/intel/cc/9.0/bin:$PATH"
export PATH

LD_LIBRARY_PATH="/opt/intel/cc/9.0/lib:$LD_LIBRARY_PATH"
export LD_LIBRARY_PATH

MANPATH="/opt/intel/cc/9.0/man:${MANPATH}"
export MANPATH

INTEL_LICENSE_FILE="${INTEL_LICENSE_FILE}:/opt/intel/cc/9.0/licenses:/opt/intel/licenses:${HOME}/intel/licenses"
export INTEL_LICENSE_FILE

```

any comments will be appreciable.

---

### Post by healychan on 2006-01-15
You should modify your /etc/bash.bashrc file.

It is a system wide file. The settings here apply to all users of your system.

---

### Post by hadian on 2006-01-16
Thanks for your reply.
the problem is that i want to the PATH i introduced in the commands be accesible out of console. i added the commands to /etc/bash.bashrc and they were active when i use console. however they are not accesible for eclipse.
when the eclipse wants to compile the code it can not find the compiler i introduced by by commands. this is the error message in eclipse console view:

make -k all 
Building file: ../hel1.c
icc -g -O0 -c -o hel1.o ../hel1.c
/bin/sh: icc: command not found
make: *** [hel1.o] Error 127
make: Target `all' not remade because of errors.
Build complete for project hello1

---

### Post by schilcha on 2006-01-16
Try ~/.gnomerc... it'll set the environment in your gnome-session.
Here's the content's of mine:
```

export R_HISTFILE=$HOME/.Rhistory
export R_HOME=$HOME/local/lib/R
export PATH="$PATH:$HOME/bin:$HOME/local/bin"

```

Don't know, if there's a system-wide file somewhere in /etc

Good Luck!

---

### Post by hadian on 2006-01-16
where is the file .gnomerc? i can not find it in my system. nether in /home nor in /etc.

---

### Post by dcer on 2006-01-16
~ stands for home dir

if the file has a dot (.) in front it's hiden. Go to View and set to display hidden files

---

### Post by hadian on 2006-01-16
i do not have this file in my home directory. i used "ls -la", but i could not find it. will it act if i create it?

---

### Post by schilcha on 2006-01-16
Just go ahead and create the file (it didn't exist on my system either). You'll need to re-login (reload gnome) to activate your changes.

... sorry for being too short in my previous post...

---

### Post by healychan on 2006-01-17
[QUOTE=hadian]when the eclipse wants to compile the code it can not find the compiler i introduced by by commands. this is the error message in eclipse console view:[/QUOTE]
I don't use eclipse for java programming therefore I don't have any ideas. The IDE i am using doesn't need to edit the $PATH variable, instead, there were a menu allows me to choose what and which complier to use for a specific language.

Perhaps you can do the same thing in the ecplise configuration menu.

---

### Post by hadian on 2006-01-18
[QUOTE=healychan]I don't use eclipse for java programming therefore I don't have any ideas. The IDE i am using doesn't need to edit the $PATH variable, instead, there were a menu allows me to choose what and which complier to use for a specific language.

Perhaps you can do the same thing in the ecplise configuration menu.[/QUOTE]
May you introduce that IDE?

---

### Post by healychan on 2006-01-19
The IDE is called geany. It is a lightweight IDE so don't expect it can do what eclipse does.

This is the home page of geany. [http://geany.sourceforge.net/]("http://geany.sourceforge.net/")

---

