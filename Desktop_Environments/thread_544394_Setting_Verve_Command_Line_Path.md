---
title: "Setting Verve Command Line Path"
date: 2007-09-06
forum: Desktop Environments
---

### Post by cujo on 2007-09-06
I've been fiddling with the Verve Command Line panel applet thing in XFCE and I have a problem.  I amend my $PATH in my .zshrc, but apparently this plugin doesn't bother with silly things like that (and why would it).  So my question is, where does it get it's $PATH from, and (if it isn't obvious), where can I change it?

---

### Post by johnraff on 2007-09-14
I'm just now struggling with the same problem. I haven't *got* a .zshrc I don't think and I've been trying to get at it from the bash end, with .bash_profile and .bashrc. This block of code is at the end of .bash_profile by default: ```
# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
     PATH=~/bin:"${PATH}"
fi
```but didn't seem to have any effect anywhere... 
When I moved it to the top of .bashrc then ~/bin was added to $PATH, but only when using a terminal. Scripts run by clicking or from a launcher are only getting the unmodified $PATH, and the verve applet likewise doesn't know anything about commands in the ~/bin directory. :( 
Getting a bit confused with login and non-login shells, (non-)interactive shells...

Anyway I'd also very much like to know how to add something to the $PATH that Verve uses, if anyone can help.

---

### Post by johnraff on 2007-09-17
cujo you might want a look at [this page](https://wiki.ubuntu.com/OneTruePath), if you haven't fixed it yet. 
I made a .pam_environment file in my home directory, put this in it:```
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games:/home/john/bin
```(ie the standard path + ~/bin) and *woo hoo* next bootup that's what my scripts, and, yes, Verve too, now use!! :)
You might be able to set other environment variables there too. I haven't yet checked if you can do PATH=${PATH}:/home/john/bin instead of writing in the whole path.

(*edit*)
I got the syntax for .pam_environment wrong; /etc/security/pam_env.conf  has the right  way.
Anyway, it looks as if that won't be supported in the near future, but... there's what looks like a better way: 
**the ~/.profile file**. Fresh installations have one apparently but I upgraded from Brezy so didn't.  You can  set any environment variable there with```
VARIABLE=whateveryoulike
``` and anyway the Verve Command Line picked up my  modified```
PATH="${PATH}":${HOME}/bin
```no problem! :)

---

