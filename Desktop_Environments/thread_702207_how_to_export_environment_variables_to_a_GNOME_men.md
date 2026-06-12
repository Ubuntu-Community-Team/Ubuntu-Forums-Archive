---
title: "how to export environment variables to a GNOME menu item command?"
date: 2008-02-20
forum: Desktop Environments
---

### Post by aikishugyo on 2008-02-20
Hello,

I am trying to get a Japanese input method to work with an application launched from GNOME. This works fine from the terminal with:

$ export LANGUAGE="ja_JP.UTF-8"
$ export LANG="ja_JP.UTF-8"
$ export LC_ALL="ja_JP.UTF-8"
$ export XMODIFIERS="@im=kinput2"
$ kinput2-canna &
$ <execute command exactly as in GNOME menu item>

However, I cannot figure out how to include the environment variable settings in the GNOME menu item command. Whatever combinations I have tried, the error is returned that the file or directory does not exist; i.e., GNOME cannot parse the combination of settings and commands. 

A search of the forums and Google did not turn up answers applicable to individual apps, only to GNOME as a whole (from control center, gdm session manager, etc.)

Any help much appreciated,
   Gernot Hassenpflug

---

### Post by aikishugyo on 2008-02-20
I received a reply from Rakshae on the ubuntu-users ML---thanks a lot!!! The solution is to put the commands into a shell script file, make it executable, and call that script from the GNOME menu.

---

