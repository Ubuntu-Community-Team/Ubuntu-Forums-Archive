---
title: "SunRay Local Keyboard Not Working"
date: 2006-02-13
forum: Desktop Environments
---

### Post by imnes on 2006-02-13
I have setup my server with Ubuntu 5.10, and the SunRay Server Software as described at:
[https://wiki.ubuntu.com/UbuntuOnSunRay](https://wiki.ubuntu.com/UbuntuOnSunRay)

Everything is working great with the SunRay terminals, but the server's local keyboard isn't working.  (It will work for maybe 10 seconds when GDM first starts up but then dies off).  If I'm quick to login sometimes I can get into gnome before it dies and works fine until I log back out.  

Anybody know what could be causing this?  (The keyboard still seems to work, the status LEDs like caps lock respond as expected.  But keypresses don't seem to be getting to GDM / X at all.  CtrlAltBackspace doesn't even do anything).

Nick

---

### Post by M3ATW0D on 2006-05-07
I have a very similar issue and also followed the wiki, although none of my keyboards work.  They all have the same symptoms.  This is my post to the sunray users list, of which i have yet to get a response.

Hi all, I'm new to the list and I cannot seem to find an answer to this anywhere.  I have installed SRSS 3.1 on Ubuntu 5.10, all is well and the  rays join the server, however I have an issue with GDM.  I followed the wiki as per: [http://wiki.ubuntu.com/SunRayOnUbuntu](http://wiki.ubuntu.com/SunRayOnUbuntu) My problem is with the keyboards.  The keyboards on the rays and the keyboard on the server all act the same way.  Once GDM comes up, I get 'Authentication Failed' messages over and over.  It looks as if the keyboard is hitting <ENTER> over an over.  When the message comes up, I can say 'OK' by hitting <ENTER> and then it just re-appears.  The only key responsive is <ENTER> and the num/scroll/caps locks can be enabled / disabled.  Other than that no keyboard works.  The sunrays appear to work in every other way.  Also, if I change to KDM, I can log into the server fine with both Gnome and KDE.  I really hope someone out there can answer / fix my issue I am having.  Thanks for any help you can provide, --Luke

---

### Post by M3ATW0D on 2006-05-08
[[ Bump ]]

---

