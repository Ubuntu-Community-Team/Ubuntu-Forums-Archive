---
title: "Some Basic Questions (that I can't find working answers to)"
date: 2004-12-14
forum: Desktop Environments
---

### Post by LoneIgadzra on 2004-12-14
I've checked the "unofficial starter guide" and given these forums a cursory once-over, and was unable to find any solutions to my problems that actually worked. I am a complete Linux neophyte (except some prolongued exposure to Mandrake, during which I experienced many problems that generally boiled down to I couldn't figure out how to get anything to work).

Question #1: How do I make Windows XP the default OS in Grubb? With Lilo and Mandrake it was easy (relatively speaking, which really isn't saying much)...

Question #2: How do I mount my windows drives on startup, in such a way that they are easily accessible? I've tried adding several different lines to the relevant file (forget what it's called), to no apparent avail. Or rather, I can access one of them if I manually navigate to /mnt/windows which is a complete pain in the ass. One drive (hdb1) has all my music on it which I want to listen to in Linux, and the other (hda1) has all my documents. I just want them to show up as normal hard drives, I don't care if they're read only.

And while I'm at it, anyone know where I can download an AAC plug-in for one of the audio players? My entire music library is made up of AAC (.m4a) files. A Google search only turns up a lot of cryptic confusing results that I don't know what to do with.

---

### Post by Daniel G. Taylor on 2004-12-14
So I'm a bit slow... I left a reply in your other thread that said not to leave a reply... go figure :-P

---

### Post by ulrich on 2004-12-15
for question 1:

edit/boot/grub/menu.lst

!!! this applies to a setup where windows is NOT hd0 !!! 
!!! if your win-hd is hd0 then kick the map commands !!!
```

title           Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
chainloader     +1
makeactive

```
also theres a parameter 'default' which lets you select which one is the default.
count the entries for the oses and enter the number for your xp. (counting starts at zero!)
and hiddenmenu should be commented.

question 2:
mount them in /media and not in /mnt.
doing so results in handy icons on your desktop, which lets you access them quickly.

question3:
no idea and too lazy to investigate :)

---

### Post by ubuntu_demon on 2004-12-15
for question 1 :

install the package grubconf
it's a graphical tool to edit the grub configuration.

In hoary there's a tool like this integrated.

---

### Post by adbak on 2004-12-15
Question 3:  Enable the Universe repo and install the package xmms-mp4.

How to enable Universe? [http://www.ubuntulinux.org/wiki/AddingRepositoriesHowto#uncommenting-universe](http://www.ubuntulinux.org/wiki/AddingRepositoriesHowto#uncommenting-universe)

---

