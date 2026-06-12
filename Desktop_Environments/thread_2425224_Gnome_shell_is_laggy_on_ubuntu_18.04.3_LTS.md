---
title: "Gnome shell is laggy on ubuntu 18.04.3 LTS"
date: 2019-08-22
forum: Desktop Environments
---

### Post by bybull on 2019-08-22
Hi everyone, I'm a new ubuntu user. I'm noticing some stutters when I'm moving windows, opening and closing animations and some tearing when playing videos on youtube using firefox. Theese things happens when I'm using gnome shell, which is the defailt DE of this distro release. Instead, after entering with gnome classic, all those graphical poor performance gone, all butter smooth and video playback on youtube seems accelerated. I runned glxinfo in both the DEs and it always says  accelerated:yes. Also vaapi 1.1.0 is installed. In gnome classic I also use many animations and fading windows, and all run smooth. So, can anyone explain me why gnome shell is so laggy?
Hardware:
Chuwi Lapbook SE 
Intel celeron N4100 UHD graphics 600
4gb RAM
30gb emmc (where ubuntu is installed)
120gb ssd

---

### Post by speartip on 2019-08-22
I can't explain why, only that you're not alone. Since Ubuntu switched from Unity to Gnome-Shell, I've found it the same. All the other 'buntus, run as smooth as silk but not Gnome-Shell. All other Distros running Gnome-Shell are the same. I would recommend Ubuntu Budgie or Linux Mint Cinnamon if you want to stick with Gnome. Otherwise KDE seems to be streets ahead at the moment.

---

### Post by bybull on 2019-08-23
I just installed linux mint cinnamon, and yes it works flawless without any lag. Thanks

---

### Post by sevendogs1337 on 2019-08-23
Gnome, among all other DE's, is the highest resource user. Normal memory usage at login with Gnome, even vanilla Gnome on other distros, is close to 1GB. Also, the lovely piece of "software" named tracker, which supposedly helps you find your files, is also a culprit for high resource usage, but I don't think it is included in Ubuntu 18.04. I do know they are bringing it back though, but no clue why...

---

### Post by speartip on 2019-08-25
> **bybull said:**
> I just installed linux mint cinnamon, and yes it works flawless without any lag. Thanks
I also found that disabling vSync in Settings / General, made Cinnamon even smoother. But that varies from system to system.

---

