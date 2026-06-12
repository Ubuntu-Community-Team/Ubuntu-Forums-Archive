---
title: "setting environment PATH??"
date: 2009-05-22
forum: General Help
---

### Post by abhilashm86 on 2009-05-22
i installed Qt 4.5 from a .bin file. i made it executable file, then i gave ./filename to install, my doubt is in document they have told that
qtdemo and qmake can be done through terminal.

```
abhilash@abhilash:~$ qtdemo
bash: qtdemo: command not found

```

my .profile looks like this, note i've added Qt path in profile, but its not working

```
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile
umask 022
# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
   	. "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"

    PATH=/home/abhilash/qtsdk-2009.01/bin:$PATH
         export PATH
    setenv PATH /home/abhilash/qtsdk-2009.01/bin:$PATH


fi
```

---

### Post by sdennie on 2009-05-22
setenv is for the C shell.  You'll need to add something like this to ~/.bashrc:

```

export PATH=/home/abhilash/qtsdk-2009.01/bin:${PATH}

```

(Then start a new terminal)

---

