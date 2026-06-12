---
title: "[ubuntu] [ubuntu_mate] Unity to MATE. Switch or reinstall OS.  16.04.1"
date: 2016-09-18
forum: Desktop Environments
---

### Post by Spud37 on 2016-09-18
I am wondering if I can switch from Unity to Mate on my install of ubuntu 16.04.1. I am currently just running ubuntu 16.04.1, this is on my laptop and am currently thinking of switching to ubuntu mate to have it run as smooth as I can and save battery life. I read that Mate is a great DE to use on laptops. I have tried to find a good guide to help switch though most I found seem to be unclear. Thanks

---

### Post by deadflowr on 2016-09-18
You can install mate and log into it from the current installation, by installing the mate desktop package:
```
sudo apt install ubuntu-mate-desktop
```
Then you simply switch between mate and unity(ubuntu) at the login screen.
(At login screen in the username/password box there will be an icon in the top right corner of said box, click on it to open the desktop options and toggle which desktop you want to log into)

The main problems you will have to deal with is bloat.
Different desktop environments will install their own set of basic packages, so while unity has a file manager and a terminal, so too does mate.
So you end up with multiple programs that do the same exact thing.

Bloat is usually why people defer to install different DEs within their own whole OS, as opposed to installing them within a single OS.(If that makes sense)

But you can install them side by side within a single OS if that is preferred.

---

### Post by Spud37 on 2016-09-22
Thanks, I may just wipe ubuntu and install ubuntu MATE. I want to try and make it a bit quicker. Thanks

---

