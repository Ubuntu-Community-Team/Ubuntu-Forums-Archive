---
title: "TAB Completion for apt-get"
date: 2009-06-04
forum: General Help
---

### Post by Nexusx6 on 2009-06-04
Hey all,

I just recently reinstalled Kubuntu 9.04. I have / and /home/ on different partitions, and I wiped /home/ clean of hidden folders and such, saving only my personal data (Music, Pictures, etc). When I went to use apt-get for reinstalling my favorite apps, I noticed I can no longer TAB complete the packages that I want to download :( Pushing TAB in attempt to completely the package name instead tries to complete the word using files in my /home/ directory.

I found sites the mention adding this to .bashrc to get tab complete working for apt-get

```
source /etc/bash_completion
```

but I noticed that after the reinstall a new .bashrc file was never made. I tried making my own and adding the line in by itself, but still no dice :( 

Any help?

---

### Post by Celauran on 2009-06-04
Copy the default one from /etc/skel/.bashrc?

---

### Post by ibuclaw on 2009-06-04
Is bash completion installed?
```
sudo apt-get install bash-completion command-not-found
```

Regards
Iain

---

### Post by Nexusx6 on 2009-06-04
> **Celauran said:**
> Copy the default one from /etc/skel/.bashrc?

Good idea :D I went ahead and did so, and appended the line for apt-get at the bottom of .bashrc, still not working. Do I have to restart?

> Is bash completion installed?
Yup, both are newest versions

---

### Post by Celauran on 2009-06-04
> **Nexusx6 said:**
> Good idea :D I went ahead and did so, and appended the line for apt-get at the bottom of .bashrc, still not working. Do I have to restart?

Try

```
source .bashrc
```

If that doesn't work, try logging out and back in.

---

### Post by Nexusx6 on 2009-06-04
> **Celauran said:**
> Try

```
source .bashrc
```

If that doesn't work, try logging out and back in.

Works :D

Thank you very much. You don't know how much you miss a feature till you don't have it anymore :redface:

---

### Post by ibuclaw on 2009-06-04
Oh, and btw, you **~/.profile** file should look like this:

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
It should be in this file where ~/.bashrc gets sourced whenever you login/open a new terminal session.

Regards
Iain

---

### Post by Celauran on 2009-06-04
> **tinivole said:**
> Oh, and btw, you **~/.profile** file should look like this:


Which can also be snagged from /etc/skel if need be :)

---

