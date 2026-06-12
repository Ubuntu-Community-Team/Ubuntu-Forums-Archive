---
title: "Fawn: bash_profile not executed from gnome_terminal"
date: 2007-05-03
forum: Desktop Environments
---

### Post by bcarp on 2007-05-03
I have scripts in my $HOME/bin and in previous versions of Ubuntu the scripts would be in my $PATH thanks to $HOME/.bash_profile  

Ever since I upgraded to Fawn 7.04 the $PATH was  not set correctly. After experimenting I found this problem only occurs when in Xwindows. If I login to a TTY the path is set correctly.

```
# ~/.bash_profile: executed by bash(1) for login shells.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile
#umask 022

# include .bashrc if it exists
if [ -f ~/.bashrc ]; then
    . ~/.bashrc
fi

# set PATH so it includes user's private bin if it exists
if [ -d $HOME/bin ] ; then
    PATH=$HOME/bin:"${PATH}"
fi
```

From Gnome:
```
bcarp@bcarp-desktop:~$ export | grep PATH
declare -x PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"

```

From TTY
```
bcarp@bcarp-desktop:~$ export | grep PATH
declare -x PATH="/home/bcarp/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"

```

What could be causing this? :confused:

---

### Post by taurus on 2007-05-03
Put it in ~/.bashrc instead.

---

### Post by bcarp on 2007-05-03
> **taurus said:**
> Put it in ~/.bashrc instead.

Thanks that worked. Should bashrc be called from bash_profile?

---

