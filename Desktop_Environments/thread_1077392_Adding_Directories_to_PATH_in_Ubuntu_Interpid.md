---
title: "Adding Directories to PATH in Ubuntu Interpid"
date: 2009-02-22
forum: Desktop Environments
---

### Post by nova47 on 2009-02-22
I was wondering how to add directories (specifically the current directory) to the PATH variable. I've tried a couple of things such as adding PATH=$PATH:. to the end of .profile but haven't had any luck getting it to work and the only info I've found hasn't been updated since dapper and I'm using Intrepid. Here is a copy of my .profile

# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022

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
fi

---

### Post by taurus on 2009-02-22
Try adding it to ~/.bashrc.

Edit ~/.bashrc

```
gedit ~/.bashrc
```
and add these two lines to the end of it.

```
PATH=$PATH:~/bin:.
export PATH
```

---

### Post by nova47 on 2009-02-26
Thanks for such a fast response. I didn't realize you also have to export the path.

---

