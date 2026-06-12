---
title: "Virtualbox &amp; iTunes"
date: 2008-11-14
forum: Desktop Environments
---

### Post by rm06 on 2008-11-14
Hello,

I've installed Windows XP on my VirtualBox so I can run iTunes. I've made it past some minor issues such as sound from the VirtualBox and installing guest additions, however I'm stumped as to how to access my current iTunes library. I've shared out a folder via VirtualBox and I've pointed my iTunes to it, but for some reason I can't get it to see the library. I've only allocated 10GB to my XP install so importing my entire library isn't really feasible.

I'm sure this is an easy fix (hopefully) though I just can't seem to get past it. Any help would be much appreciated.

Thanks,
Ryan

ps - I'm running 8.1 if it matters

---

### Post by rm06 on 2008-11-14
Anyone?

Bueller?

---

### Post by huanix on 2008-11-16
I'm not exactly sure what your condition is, but it sounds like a windows networking issue. I directed iTunes to my music on my linux drive by creating a network location and then mapping that drive to a drive letter.

Try this:
1. Start the windows virtual machine.
2. On the Windows desktop, right click -> New -> Shortcut
3. the name for the shortcut will be the network path to your music.. mine is \\192.168.1.3\music
4. When you get that correct, you will enter credentials for ubuntu, tell it to save the login.
5. right click on that shortcut and "Map Network Drive..." to a drive like Y:, and check reconnect at login. 
6. In iTunes, open Edit > Preferences > Advanced
7. Click "Change" and navigate to your new networked drive.

It should all work out now... ...

---

### Post by arcane14 on 2009-05-24
> **huanix said:**
> I'm not exactly sure what your condition is, but it sounds like a windows networking issue. I directed iTunes to my music on my linux drive by creating a network location and then mapping that drive to a drive letter.

Try this:
1. Start the windows virtual machine.
2. On the Windows desktop, right click -> New -> Shortcut
3. the name for the shortcut will be the network path to your music.. mine is \\192.168.1.3\music
4. When you get that correct, you will enter credentials for ubuntu, tell it to save the login.
5. right click on that shortcut and "Map Network Drive..." to a drive like Y:, and check reconnect at login. 
6. In iTunes, open Edit > Preferences > Advanced
7. Click "Change" and navigate to your new networked drive.

It should all work out now... ...

I am also running music from Ubuntu (Jaunty) into iTunes via virtualbox win xp. I have successfully shared a folder and mapped it as a drive in xp. But when I import the music folder, it stops at 4333 songs, 23.93 GB. However, I know I have over 8000 songs and over 50 GB in the actual folder. The vdi is only 10gb for xp, but I'm not copying the files to xp, just adding them to the library/iTunes db. Don't know why the process truncates where it does. Any advice?

---

### Post by Sarai the Geek on 2009-05-24
Make sure that in iTunes you have your library set to "manual" for the management settings- otherwise whenever you add something to your library it will automatically add it to the iTunes folder... annoying!

---

### Post by chaumurky on 2009-09-26
Resurrecting this thread since I too have this issue. I set up a virtualbox shared folder  pointing to /media/files/audio and in windows mapped it to m: but when I try to import the whole drive i get about 5 artists. If I repeat the import it only sees the same ones.

Maybe I need to open each folder in explorer so it sees all of them or something like that. I'm in the process of checking off 'read only' recursively so it has to go through each file but this will take a while. Also ran chmod 777 -R /media/files/audio' just in case.

---

### Post by jacrider on 2010-01-07
Sorry to resurrect this thread once again, but here goes.

I am running 9.10 on my computer and have WinXP (valid license) running in VirtualBox 3.1.2.  I have installed iTunes (the only reason I have XP) in XP.

My wife's iMac has our entire media library stored on it.  She has Sharing enabled over the network.

I can see the shared library once I start iTunes in VirtualBox, but shortly thereafter, it vanishes from the iTunes navigation bar on the left and I can't seem to get it back.

Has anyone had any luck with this?

Thanks.

---

### Post by jacrider on 2010-01-08
I have confirmed that my daughter's MacBook can see our shared library and can stream content to her computer.

Any ideas why I can't do this through VirtualBox?

Thanks.

---

### Post by Pablo Pablovski on 2010-01-08
It could be the networking config in Virtualbox - if you're using the machine's Ethernet port in NAT mode, it's likely to block incoming traffic, preventing sharing. 

Try setting the networking mode in Virtualbox to "bridged". Can't recall exactly where you do that, but you could have a browse on the VB support site if you're stuck.

[http://forums.virtualbox.org/](http://forums.virtualbox.org/)

Good luck!

---

### Post by jacrider on 2010-01-10
Perfect!!!

Many thanks.  Now I can stream from our iTunes library.  Life is great.

---

### Post by kseise on 2010-01-18
> **chaumurky said:**
> Resurrecting this thread since I too have this issue. I set up a virtualbox shared folder  pointing to /media/files/audio and in windows mapped it to m: but when I try to import the whole drive i get about 5 artists. If I repeat the import it only sees the same ones.

Maybe I need to open each folder in explorer so it sees all of them or something like that. I'm in the process of checking off 'read only' recursively so it has to go through each file but this will take a while. Also ran chmod 777 -R /media/files/audio' just in case.


I am having this problem also.  Did you ever figure out what the problem was, or did you get it to work?

---

