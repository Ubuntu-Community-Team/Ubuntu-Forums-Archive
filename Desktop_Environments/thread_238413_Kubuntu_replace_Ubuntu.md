---
title: "Kubuntu replace Ubuntu"
date: 2006-08-17
forum: Desktop Environments
---

### Post by carllfo on 2006-08-17
I have decided to install Kubuntu, currently running Ubuntu, and want to do this as a fresh install WITHOUT losing some files I have in /home/USERNAME/.
Is this possible?
I do have a small NTFS partition that I can write to it's just that it takes ages and would like to know if there is another way.

---

### Post by catlett on 2006-08-17
You do not have to run an installer to get kubuntu. You can install the kubuntu "package" along side ubuntu. They are the same thing. The difference is the window manager. Ubuntu uses gnome and kubuntu uses kde.
You can have more than one window manager in linux.
To install kubuntu open the terminal and enter
```
sudo aptitude install kubuntu-desktop
``` This will install kubuntu.
Now you can do 1 of 2 things. Keep both. All you have to do to switch between them is to select "options" at the login screen and then select "change session". Choosing Gnome will log you into ubuntu and choosing kde will log you into kubuntu.
The other is you can remove ubuntu and just keep kubuntu. Reboot and select kde to get into the kubuntu desktop. Open up the konsole and enter
```
sudo aptitude remove ubuntu-desktop
``` Now you will have kubuntu with all your files from ubuntu but ubuntu/gnome will be gone.
The choice is yours but you do not have to install kubuntu from an installation cd.

---

### Post by bulldog on 2006-08-17
Take a look here.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

You don't have to do a fresh install just to go to Kubuntu.
Install Kubuntu as discribed and if, you want, remove your ubuntu.

Writing to a NTFS file system is not without danger!
Can't recommend it,and I for sure, will not do so.

---

### Post by carllfo on 2006-08-17
I'm not having any problems using ntfs-3g.

The reason I want to do a fresh install is that I seem to have an unresolvable sound problem (searched everywhere and no answers helped my situation), also I have tried the kubuntu desktop and prefer it.

I have moved the essential files onto my ntfs partition and am now doing a fresh kubuntu install.  Thanks for the help and suggestions :)

---

### Post by dirtylobster on 2006-08-17
> **carllfo said:**
> I have moved the essential files onto my ntfs partition and am now doing a fresh kubuntu install.  Thanks for the help and suggestions :)

Hopefully you remembered to include all the hidden files, that's where most of the program settings are.

Did everything go well?

---

### Post by carllfo on 2006-08-17
The essentials were personal files, yes it went smoothly :D

---

