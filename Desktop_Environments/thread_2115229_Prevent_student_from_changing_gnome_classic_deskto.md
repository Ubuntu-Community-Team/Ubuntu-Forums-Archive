---
title: "Prevent student from changing gnome classic desktop background on Edubuntu 12.04"
date: 2013-02-12
forum: Desktop Environments
---

### Post by wittyman37 on 2013-02-12
I am currently a technology coordinator in my school in the Bronx, USA.  I have 22 desktops in a computer lab running Edubuntu 12.04 32-bit.  I want to prevent these students (standard user) from being able to change the desktop background.  

I tried installing and using gconf-editor and going to gnome>desktop>background and right clicking on the background image key, clicking "Set as Mandatory" and entering the admin password.  There was no indication it went through, and even after a system reboot, I could change the background simply by right clicking on the desktop, choosing "change desktop background" and clicking on any other image.  

What am I doing wrong?!?  ](*,)Please help!

---

### Post by zombifier25 on 2013-02-12
Try doing what outlined [here](http://www.novell.com/support/kb/doc.php?id=7007945), which is exactly what you need.

---

### Post by wittyman37 on 2013-02-12
> **zombifier25 said:**
> Try doing what outlined [here](http://www.novell.com/support/kb/doc.php?id=7007945), which is exactly what you need.
[zombifier25]("http://ubuntuforums.org/member.php?u=1251447"), thank you for your quick repsonse!  I just tried this, and no errors were reported.  However, it did not work and I could easily change the background by right clicking on the desktop, choosing "change background" and selecting any image.  

Any other ideas?  I read somewhere that gconf has been replaced by dconf?  I tried following the directions here <https://live.gnome.org/dconf/SystemAdministrators> with no luck. 
:(

---

### Post by wittyman37 on 2013-02-12
Is it possible since this is a gnome classic fall back desktop on Ubuntu 12.04, that I need to edit compiz?  I know little of this, so if this is the case, can someone point me to a tutorial to lock the background image (wallpaper) so students cannot change it?

---

### Post by wittyman37 on 2013-02-12
dconf does not seem to be installed on edubuntu by default.  I tried  installing it and following the guide to create the site and local  defaults and then create the lock file inside the specified directories  (I had to create all directories myself).  That did not work :(

---

### Post by wittyman37 on 2013-02-14
So I have found a workaround for now.  I can add a startup item that runs the following command:

```

gsettings set org.gnome.desktop.background picture-uri "file:///usr/share/backgrounds/edubuntu_default.png"

```

This will change the desktop background back each time the user logs in (or boots up).  This is not perfect, but it will work until I find a real way to completely block the user from changing the background image like I can in Windows 7.

---

