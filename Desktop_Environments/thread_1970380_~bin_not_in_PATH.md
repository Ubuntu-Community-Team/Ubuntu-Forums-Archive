---
title: "~/bin not in PATH"
date: 2012-05-01
forum: Desktop Environments
---

### Post by bobthe on 2012-05-01
I recently installed 12.04 LTS dual boot.
I wanted to add something to the PATH, so i decided to just put it in the ~/bin directory as it is already added to the path everytime a bash shell is open (due to the .profile file). but this is not the case for me. 

My .profile contains the code to add ~/bin to the path everytime a new session is open. Here is a copy of the entire .profile : 

```

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

```

So it should be adding the /bin into the path. but once i print the value of PATH, i get this:

```

/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```

This doesn't include the ~/bin directory. what should i do?

---

### Post by bobthe on 2012-05-01
NEVERMIND IT WORKS NOW! i think its because I updated and restarted, now I'm able to see my ~/bin in the PATH.

---

### Post by markbl on 2012-05-01
> **bobthe said:**
> NEVERMIND IT WORKS NOW! i think its because I updated and restarted, now I'm able to see my ~/bin in the PATH.
The reason is because only login shells read ~/.profile, and only if ~/.bash_profile does not exist (see INVOCATION in man bash). Your X desktop environment would have read ~/.profile when it started.

---

