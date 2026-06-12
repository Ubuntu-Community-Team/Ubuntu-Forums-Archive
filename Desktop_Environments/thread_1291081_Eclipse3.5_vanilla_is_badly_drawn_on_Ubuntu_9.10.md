---
title: "Eclipse3.5 vanilla is badly drawn on Ubuntu 9.10"
date: 2009-10-14
forum: Desktop Environments
---

### Post by _iago on 2009-10-14
I have downloaded Eclipse 3.5 SR1 from eclipse.org this morning.
While trying to install some plugins I have noticed that all the treeviews are badly drawn.
I have tried switching the default java VM from java-6-openjdk to java-6-sun (to other alternatives), but this hasn't improved the behavior.

somebody else has this kind of problem?

----Steps to reproduce
open eclipse
help\install new software
eventually add some plugin download site using the "available software sites" link
select one of the sites, wait for the completion of the packages description download (a small progress bar is shown in the lower-left corner of eclipse)
the list is kept empty at the end of the download, but if you pass the mouse on the blank area the details line is filled with some text.

---

### Post by raptor3D on 2009-10-14
May be you should try installing it with synpatic...
Just try it..
It worked for me (ubuntu 8.10)

---

### Post by _iago on 2009-10-14
yes, it worked in the sense that now I haven't anymore the possibility to check for updates or install new software via eclipse.
a message 
```
Cannot complete the request. This installation has not been configured properly for software updates.
```
is prompted instead of the software updates manager.

---

### Post by _iago on 2009-10-14
regarding the problem of the update manager not starting, on this other [post]("http://swiss.ubuntuforums.org/showthread.php?p=8027574") ([http://swiss.ubuntuforums.org/showthread.php?p=8027574](http://swiss.ubuntuforums.org/showthread.php?p=8027574)) somebody proposes two solutions:
[LIST]
[*] install a vanilla version (which leads me to the problem described initially)
[*] install the plugins as root (I've tried this, but I'm getting the same messagebox, with the same message).
[/LIST]

---

### Post by leohart on 2009-10-25
I would like to add to thumb up on this problem as well. I have the same problem and it bugs me to no end.

I don't think installing Eclipse from Synaptic is a possible solution since I need to be able to install plugins. But the behavior of plugin installation is erratic.

Even in eclipse 3.4, clicking on the Install button after selecting a package does not do anything. No message on the console, no change in the GUI, just nothing. WTH.

---

