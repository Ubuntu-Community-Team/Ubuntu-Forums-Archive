---
title: "start up script of some sort ??  Help."
date: 2009-03-22
forum: General Help
---

### Post by BillyPrefect on 2009-03-22
I need to run these commands, in this order, when Ubuntu starts.


root@billy-laptop:/home/billy# rmmod b44
root@billy-laptop:/home/billy# rmmod ssb
root@billy-laptop:/home/billy# modprobe wl
root@billy-laptop:/home/billy# modprobe b44
root@billy-laptop:/home/billy# modprobe b43

When I run lshw -C network before these commands, my wireless is being driven by ssb.  You have to disable b44, b43 before you can disable ssb, ... 

then I run the modprobe command lines and run lshw -C network, and my wireless is there and listed, it can connect to the network, and I am able to plug into a wired network correctly.

Any help would be appreciated.  Noob, trying to get a handle on broadcom wired and wireless network cards.

*EDIT* I am using Intrepid, Dell 1720 with broadcom wired card and broadcom wireless 4328 card.  

Also, I just noticed that my wired card now says unmanaged... but am happy with having wireless as it is.

---

### Post by Xiong Chiamiov on 2009-03-23
Make a text file with this in it:
```

#!/bin/sh
rmmod b44
rmmod ssb
modprobe wl
modprobe b44
modprobe b43

```
then follow [these](https://help.ubuntu.com/community/UbuntuBootupHowto) or [these](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/) instructions.

---

### Post by cariboo on 2009-03-23
Why not blacklist the drivers you don't want to load?

The blacklist file is located in /etc/modprobe.d, you can edit the file by pressing Alt-F2 and typing:

```
gksu gedit /etc/modprobe.d/blacklist
```

it is pretty self evident how to add drivers to the blacklist.

Jim

---

### Post by BillyPrefect on 2009-03-23
But I don't want to blacklist completely... I want to disable to change the load order really.  B44 loads SSB, SSB sucks for my broadcom wireless, so I have to disable B44 to disable SSB, then load the WL (or WL0), then reload B44 for my wired connection to work.

Also I have read somewhere that it is impossible to blacklist ssb, it will reload everytime no matter what is done.

---

