---
title: "configure xorg for Dell wide-screen monitor to get full resolution"
date: 2007-08-26
forum: Dell  Ubuntu Support
---

### Post by magicsowon on 2007-08-26
I am a new ubuntu user and I recently installed kubuntu on my desktop. 

I have a Dell 2407WFP-HC monitor and a Ati Radeon x1300PRO. 

My problem is that I cannot find a driver for this card and I cannot configure xorg to support 1920x1200, which is the monitor native resolution. I would appreciate any help.

---

### Post by JayEmm on 2007-08-27
Hi,

As far as I am aware you will need both the restricted-drivers package and xorg-driver-fglrx.
FGLRX is the name of the Ati driver. It SHOULD support your card and resolution.
Messing about in xorg isn't always recommended, but you can tell it to use those resolutions.

I believe the terminal command is

# dpkg-reconfigure xserver-xorg

or similar anyway.

Try doing it in the GUI before anything else.

James.

---

### Post by magicsowon on 2007-08-29
Actually, I messed a lot with xorg.conf, only to find out many ways to screw up the computer even further. My conclusion is that I still need the video-card driver - by the way, the machine can boot in windows, where I get the right resolution, only I wouldn't switch to it just for that.

---

### Post by magicsowon on 2007-09-18
I, somehow, found the solution. 

1. I uninstalled the old fglrx drivers.

2. download the ati drivers:
[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html) 

3. sudo ./ati-driver-installer-8.40.4-x86.x86_64.run

4. enable the restricted drivers:
"System -> Administration -> Restricted Drivers Manager" and select "ATI accelerated graphics driver"

- I still don't know how to do this in kubuntu kde - so I got it from the gnome desktop menu. I would appreciate if anyone told me how to do this from command line.

This is the step at which xorg.conf is rewritten.

5. reboot - in safe mode
disable the option "Composite" in xorg.conf

6. sudo /etc/init.d/kdm start

All that I did was suggested on this page:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by magicsowon on 2008-02-02
Yesterday, I switched to Ubuntu 7.10. The ati card problem appeared again, and I could not fix it using my old method. However I found 
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)
and just followed the instructions. Now it's working.

---

