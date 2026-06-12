---
title: "Grub order of booting"
date: 2009-02-05
forum: General Help
---

### Post by rweaver4 on 2009-02-05
Because of my work I need to use windows XP most of the time. Is it possible to partition a disk with XP already installed, install Ubuntu and then change the boot order in grub so that XP is the automatic first boot seledtion?

---

### Post by feelshift on 2009-02-05
```
sudo gedit /boot/grub/menu.lst
```
There is a line "default 0", change 0 with the number of Windows entry (after "## ## End Default Options ##")
Start county with 0. I have it set to 6, that's my Windows entry after all updates (kernel update). Good luck.

---

### Post by jerome1232 on 2009-02-05
Yes this is all very possible to do :)

The easiest way is to install startupmanager within ubuntu, it's a nice gui for managing your /boot/grub/menu.lst file (this is the file that controls grub). It'll let you select the default OS along with the timeout to wait for interference and a host of other options.

You can use the synaptic package manager to install it easily enough.

(System-Administration-Synaptic Package Manager, search for "startupmanager" and mark it for installation.

---

### Post by Bigneil on 2009-02-05
this thread may be helpful;)

[http://ubuntuforums.org/showthread.php?t=986611](http://ubuntuforums.org/showthread.php?t=986611)

---

### Post by konqueror7 on 2009-02-05
> **jerome1232 said:**
> Yes this is all very possible to do :)

The easiest way is to install startupmanager within ubuntu, it's a nice gui for managing your /boot/grub/menu.lst file (this is the file that controls grub). It'll let you select the default OS along with the timeout to wait for interference and a host of other options.

You can use the synaptic package manager to install it easily enough.

(System-Administration-Synaptic Package Manager, search for "startupmanager" and mark it for installation.

easiest way!

---

