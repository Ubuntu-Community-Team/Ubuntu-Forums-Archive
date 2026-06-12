---
title: "Strange Behaviour in .gnomerc"
date: 2006-11-16
forum: Desktop Environments
---

### Post by joshmachine on 2006-11-16
Hello everybody.

I have a .gnomerc I use to set up some environment variables.  This script uses
pushd and popd to navigate around so I can source various scripts.

After upgrading to edgy this no longer seems to work.  Doing some rudimentary debugging shows that pushd is not actually changing directories.  this has me completely baffled.  Anyone have any ideas?

Thanks.

---

### Post by jojopaderes on 2006-11-28
I also have a similar problem using .gnomerc for loading up my .bash_profile environment variables. All of my Java-related environment variables are defined at .bash_profile. In order to launch Java applications on Gnome, the environment variables defined at .bash_profile need to be loaded, hence I created a symbolic link .gnomerc

Prior to upgrading to Edgy Eft, this approach worked well. Now I'm sitting ducks... :(

---

### Post by mannheim on 2006-11-29
I think this may be caused by the switch from "bash" to "dash" as the shell. In edgy, /bin/sh is a symlink to /bin/dash. So dash is the shell that sources the commands in .gnomerc, not bash.

The dash shell does not understand pushd and popd, so you can't use those in .gnomerc under edgy. The solution is either to rewrite your .gnomerc so that it is dash-compatible, or to alter the symlink /bin/sh so that it points to /bin/bash. I don't know if the latter has any negative side-effects under edgy.

---

### Post by kkvenkit on 2006-12-12
It definitely is related to the switch to dash as the default sh implementation.

I previously had *source .bash_profile* in my .gnomerc to run the script bash runs when you log in. 

The same behavior can be had even easier: just launch a login bash shell that terminates. To do this I place *bash -l -c echo* in .gnomerc: the *-l* tells bash to make it a login shell (so your .bash_profile runs), the *-c echo* specifies a command to run and then exit the shell. *echo* was chosen because it's computationally inexpensive.

---

