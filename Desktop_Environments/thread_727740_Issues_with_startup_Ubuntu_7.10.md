---
title: "Issues with startup Ubuntu 7.10"
date: 2008-03-18
forum: Desktop Environments
---

### Post by Stonerz on 2008-03-18
I have recently installed Ubuntu 7.10 on my laptop. It has worked perfectly and I have been very happy with the installation. Yesterday, it told me about updates that could be downloaded, which I decided to go ahead with. Unfortunately, near completion of the updates the computer crashed (i think due to an overheating problem which was recognised by Ubuntu and so computer automatically shut down). 

I left it for 20 minutes to cool down and restarted. Ubuntu loaded exactly the same as before and got to the login screen. When I logged in, we came to the same brown background waiting to load into the desktop. Unfortunately, it never loads to the desktop just stays on the brown screen with the mouse pointer. I have waited at this point for over an hour and nothing happens. I guess that during the update process, it must have failed during a critical element and so cannot load up the desktop as before. 

As a novice to the Ubuntu system, I am not sure if there is some way to restore back to preupdates, something i can use in a terminal to get it to complete the update? I am not sure it has even loaded the required wireless element to allow me to connect to the internet?

The distro is Ubuntu 7.10 Gutsy Gibbon.

Any help would be much appreciated

---

### Post by Patb on 2008-03-18
Stonerz.  Try starting in recovery mode.  Then try to complete the update by 
```
apt-get update
apt-get upgrade
```
With luck, your overheating problem will not strike twice.  If it does, a bucket of water will not be the correct solution. ;)

Then try restarting in normal mode with Control-Alt-Delete.  

If this does not work, repost.  

Cheers, Pat.

---

### Post by Stonerz on 2008-03-18
thanks that has worked, also had to use dpkg to recover the unfinished update. the overheating was annoying, i had xp on the laptop and it overheated all the time. I thought before slinging the laptop ill try linux. I have had it running for hours at a time with no overheating but it seems the update stressed it out a little. still, i will persevere!!!! :KS

---

