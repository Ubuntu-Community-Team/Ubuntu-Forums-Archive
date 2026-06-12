---
title: "Ubuntu updates doesn't seem to work."
date: 2005-11-17
forum: Desktop Environments
---

### Post by supertech on 2005-11-17
Hi everyone!

I am a Ubuntu newbie and I have finally successfully installed it onto my hard drive.  I am having a problem with the automatic updates.......I think.......what happens is that I am prompted when Ubuntu starts.....Breezy Badger......that there are updates available at the top right of the screen and to type in my password which I do.  The window disappears and then thats it.......when I try clicking on the Icon in the top right corner it shows me a menu to install, package manager, show, preferences, etc,.  However this window is now non responsive as I try to access anything I hear the drum and thats it.......nothing else happens.....can anyone help me?

---

### Post by adwait on 2005-11-17
Try this
```
sudo synaptic
```
Any errors?


Or, you can entirely bypass synaptic and just upgradde via commandline using
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by supertech on 2005-11-19
Thank you verrrrrryyy much.  That seemed to do the trick and got me started exploring this new world of linux.  I also reinstalled Ubuntu and this time everything worked.  I am now trying to learn and understand the set of commands that you sent me.  Thank you again, it helped a great deal........Synaptic is very user friendly.

---

