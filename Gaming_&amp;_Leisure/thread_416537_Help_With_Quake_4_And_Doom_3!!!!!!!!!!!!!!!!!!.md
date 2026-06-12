---
title: "Help With Quake 4 And Doom 3!!!!!!!!!!!!!!!!!!"
date: 2007-04-21
forum: Gaming &amp; Leisure
---

### Post by metalblitz84 on 2007-04-21
I am brand new to ubuntu and am wanting to install both doom 3 and quake 4 for it. I know just about nothing of linux right now. I have found several tutorials and web pages on how to install them, but they are too confusing and none of them are working right. I desperately need someone to help be get these installed and working, but I need the most simple step by step dumbed down instructions I can possibly get. Any help would be greatly appreciated beyond forever!!!! Thanx!!

---

### Post by meng on 2007-04-21
Firstly, what video card do you have, and have you got 3d acceleration enabled?
The installation procedure for Doom3/Quake4 should be fairly straightforward (download and run the binary .sh file from id software, then add the data files from the original CD).

---

### Post by chiefwhosm on 2007-04-21
If you have Ubuntu 7.04 then to install your 3d drivers (nvidia definately, and no doubt others such as ATI as well) then from the desktop go:

Administration>Restricted Driver Manager

load it up, it will present you with a list of hardware which can use restricted drivers, check the Enable box next to your graphics card if it's listed, apply, and ubuntu will download and install the drivers, then tell you to reboot.

Then install doom3 as the other person has said :) 

Download the .sh to your Desktop

Open a Terminal window and type,

sh *.sh

and hit enter, and follow the instructions. I've never installed doom3/quake 4, but im guessing you won't have to sudo it, however someone is sure to correct me on this point :)

---

### Post by Sockerdrickan on 2007-04-21
You need sudo if you install in root/usr/local/games dir ofcourse :D

---

### Post by lakersforce on 2007-04-21
> **Tux0r said:**
> You need sudo if you install in root/usr/local/games dir ofcourse :D

But it is not neccesary to install in /usr/local/games! If you don't use sudo it will simply install in your /home/username/ which is much simpler to handle.

---

