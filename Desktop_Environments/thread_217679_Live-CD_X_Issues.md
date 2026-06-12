---
title: "Live-CD X Issues"
date: 2006-07-17
forum: Desktop Environments
---

### Post by jaywatkins on 2006-07-17
Hello,

This topic has been posted else-where, but no suitable resolution seems to fix the problem.  

I am trying U606 out on a Dell Optiplex GX260 desktop with integrated everything.  I would like to dual-boot with Windows XP Pro SP2.  The screen resolution is currently set at a max. of 640x480.  This way, the install process cannot even start because the window is not fully visible.  I tried editing the Xorg.conf file, but was unable to save the changes as the Live-CD appears to have no root account. 

How can I set the resolution to a usable level

Thanks

/J

---

### Post by asplode on 2006-07-17
I suppose you could try 
```
sudo dpkg-reconfigure xserver-xorg
```
and select a higher resolution
(sudo is the admin prepend instead of a root account)
and then CTRL+ALT+BKSPACE to restart the desktop manager.

I'm still a novice, but that sounds like it might work.

---

### Post by jaywatkins on 2006-07-17
It sounds like a great idea, but the sudo tool will ask for a password.  What's the default sudo password?

Thanks

/J

---

### Post by jaywatkins on 2006-07-17
The previous suggestion crashed the X-server completely.  Great idea though.

Thanks

---

### Post by jaywatkins on 2006-07-18
I did an install by guessing the tab position of the next-back-cancel buttons, but the screen resolution problem still exists.

How would one set a 1024x768 resolution on a Dell Optiplex GX260?

/J

---

### Post by asplode on 2006-07-18
What option are you using to load the Live CD, option 1 or 2?  Option 2 is safe video mode, I believe.  Whichever one you're trying, try the other one and see if it helps at all.  I also believe there is a command (f5) i think to change the VGA mode when you are booting the live cd as well.  I'm currently loading the live CD on a Dell Optiplex GX60, I'll let you know how it turns out.

> **jaywatkins said:**
> I did an install by guessing the tab position of the next-back-cancel buttons, but the screen resolution problem still exists.

How would one set a 1024x768 resolution on a Dell Optiplex GX260?

/J

---

### Post by jaywatkins on 2006-07-18
I have tried both options and got the same results.  I installed U606 to the HDD and ran the update.  perhaps there is an update to X in there?

/J

---

### Post by asplode on 2006-07-18
Oh, so you've got it installed to your hard drive?  Thats good.

I suppose it depends on what kind of processor you have as to which guide you follow...

[Setup for Savage Drivers for Intel w/Hyperthreading]("http://doc.gwos.org/index.php/Install_Savage_driver_Intel_HT")

[Setup for Intel without Hyperthreading]("http://doc.gwos.org/index.php/Install_Savage_driver_Intel_NONHT")

[Setup for AMD]("http://doc.gwos.org/index.php/Install_Savage_driver_AMD") (Dells dont use AMD, do they?)

[Old skool legacy chipset setup]("http://doc.gwos.org/index.php/Install_Savage_driver_generic")

[Enabling DRI for old skool savage chipsets]("http://doc.gwos.org/index.php/3D_Graphic_Cards_Dapper")

If I had to guess, I would say follow the Intel guide without hyperthreading, unless you know for certain your processor has it.

---

### Post by jaywatkins on 2006-07-18
Smoked it!

I tried to add a "monitor" section to my xorg.conf, and when I restarted, X failed.  Back to the command line...

Time to reinstall!

Ubuntu 6.06 sux...

---

### Post by asplode on 2006-07-18
no need to reinstall...
just reconfigure the xorg.conf file, OR if you saved a backup (which is a good habit to get into) then you just replace the edited one with the backup.

If you didnt make a backup, I reintroduce you to the command
```
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm restart
```

That should get you back into GNOME, where you can follow one of the guides for the video drivers.

---

### Post by jaywatkins on 2006-07-19
A BIOS update was what I needed.  I did try the 855resolution fix, but it did not solve the overall problem.

Thanx

/J

---

