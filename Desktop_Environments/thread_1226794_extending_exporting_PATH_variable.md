---
title: "extending exporting PATH variable"
date: 2009-07-29
forum: Desktop Environments
---

### Post by Menyus on 2009-07-29
Can someone please tell me where ubuntu stores environment variables. I am running Ubuntu 9.04 and the Gnome desktop. I need to extend and export the PATH variable so that I can use Qt/Embedded I just installed. According to the instructions I need to edit the .profile file. I found "profile" and "dot.profile" in /usr/share/base-files. Is "profile" the file I need to edit?
Thanks a bunch.

---

### Post by bryonak on 2009-07-30
For all users there's /etc/environment.
And /etc/profile or /etc/bash.bashrc are fine too for exporting PATHs.

If it's just for you, here's a hint:

```
cat ~/.profile
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f ~/.bashrc ]; then
	. ~/.bashrc
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi

```

The last block appends ~/bin to the PATH variable.

---

### Post by Menyus on 2009-07-30
Thanks for the advise. I edited the /etc/environment file since it's for all users.

Also, I am not familiar with Linux shell scripting but I assume if I wanted to extend/export path like this

PATH=/usr/local/Trolltech/QtEmbedded-4.5.2-arm/bin:$PATH
export PATH

the script would look like this

# set PATH so it includes QtEmbedded bin if it exists
if [ -d /usr/local/Trolltech/QtEmbedded-4.5.2-arm/bin ] ; then
    PATH=/usr/local/Trolltech/QtEmbedded-4.5.2-arm/binn:"${PATH}"
export PATH
fi

Does this make sense?
Thanks

---

### Post by bryonak on 2009-07-31
> **Menyus said:**
> Thanks for the advise. I edited the /etc/environment file since it's for all users.

Also, I am not familiar with Linux shell scripting but I assume if I wanted to extend/export path like this

PATH=/usr/local/Trolltech/QtEmbedded-4.5.2-arm/bin:$PATH
export PATH

the script would look like this

# set PATH so it includes QtEmbedded bin if it exists
if [ -d /usr/local/Trolltech/QtEmbedded-4.5.2-arm/bin ] ; then
    PATH=/usr/local/Trolltech/QtEmbedded-4.5.2-arm/bin[color=red]n[/color]:"${PATH}"
export PATH
fi

Does this make sense?
Thanks

Looks fine except for the typo ;)

You probably know that, but I'll repeat that it's strongly recommended to always specify the interpreter (bash, sh, zsh, ...) in shellscripts, which is done with '#!' on the **first** line.
Then your export-qt-path.sh might look like this:
```

#!/bin/bash

# set PATH so it includes QtEmbedded bin if it exists
QTEMBEDDED = '/usr/local/Trolltech/QtEmbedded-4.5.2-arm/bin'
if [ -d $QTEMBEDDED ] ; then
    export PATH="${QTEMBEDDED}":"${PATH}"
fi

```

---

### Post by Menyus on 2009-07-31
Thanks again, you've been a great help!

As a side note, don't assume that I know anything. The sad truth is, I've been experiemneting with Linux on and off since the mid '90s but I always ended up abandoning it because of time constraints. (I eventually had to stop fiddling and just get things done because of dealines.) It's been very frustrating for me because I would love to run nothing but open source. 
-C

---

