---
title: "Desktop Flickers Black on Loading"
date: 2009-05-31
forum: General Help
---

### Post by apirateslife on 2009-05-31
I am a new user with relatively slim knowledge of Linux, and I'm hoping someone here can help me.  I loaded Kubuntu 9.04 on my home-built desktop yesterday.  I was having some issues with the video card/drivers (ATI Radeon HD 3200), but thought I had them worked out.  When I turned it off last night, it seemed to be working fine.  This morning, I booted up, and the screen started flickering black as soon as the GUI for Kubuntu came up!  I'm pretty sure this is a software problem, since I can see the mouse moving around the screen ...it's just the desktop that doesn't load.  The screen only flickers on about every 10-20 seconds, and only for about 2 seconds.

Any help would be much appreciated!

---

### Post by Legace on 2009-05-31
Did you install the FGLRX ATi drivers?

---

### Post by pastalavista on 2009-05-31
One possible solution... reboot in recovery mode, open root terminal and enter```
sudo dpkg-reconfigure xserver-xorg
```then reboot.

---

### Post by apirateslife on 2009-05-31
pastalavista, I tried that, and now it won't load the desktop at all, i.e. the Kubuntu load screen loads, flickers off, and then I've got a black screen with a couple of neon lines near the top.

Legace, I loaded the driver that showed up in the hardware drivers menu (I think this is the FGLRX driver?).  I did this with an earlier install of Ubuntu and had no problems.  I thought that I had rebooted without any problems since I loaded it in Kubuntu, but maybe not?

I may just try a clean reinstall of the entire OS, since that only takes about 20 minutes.

---

### Post by Legace on 2009-06-01
> **gocek said:**
> 
BTW: if you fail to boot up your Ubuntu, just reboot it, select "recovery mode" in boot-manager (GRUB) and then go for "root shell" option. 
After that just type:
```
sudo apt-get remove xorg-driver-fglrx
```

Now you will need to restore your original settings, so either restore any backed-up copy of file /etc/X11/xorg.conf or run something like:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

or another one (you will have to answer a few simple questions)
```
sudo dpkg-reconfigure xserver-xorg
```


then type
```
exit
```

and select "resume normal boot"

This should get you back to your Ubuntu desktop, but running on default drivers.

And this is how to install the drivers properly:
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_restricted_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_restricted_drivers_manually)

and do the "manual installation" STEP BY STEP.

---

