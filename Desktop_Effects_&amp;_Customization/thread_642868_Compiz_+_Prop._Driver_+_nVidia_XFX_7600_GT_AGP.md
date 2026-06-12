---
title: "Compiz + Prop. Driver + nVidia XFX 7600 GT *AGP*"
date: 2007-12-17
forum: Desktop Effects &amp; Customization
---

### Post by Andruk Tatum on 2007-12-17
Hello, I am having trouble installing the proprietary drivers for my video card.  It is an nVidia XFX GeForce 7600GT AGP card, and I fear that the AGP is the problem.

When I use the restricted-drivers-manager, it downloads and installs the latest version (100.something, i think) and then proceeds to tell me to reboot.  i do, and it loads into gnome, and then freezes, completely.  i cant even ctrl+alt+f1 or anything.

this same thing also happens with the driver i download from nvidia.com.

i am left to hard reboot.

any help is greatly appreciated.

my xorg.conf is attached.

-andruk

---

### Post by NateMan on 2007-12-17
its seems as if you do not have the nvidia drivers installed. here is the section of my xorg.conf that shows my geforce. 
Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8600M GT]"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

there are also several other areas with reference to my nvidia card. you should have these in your files. try installing the restricted drivers from terminal.

---

### Post by Andruk Tatum on 2007-12-17
Sorry, I didn't consider myself a n00b, but I've never heard of that before.

How do you do that?

Thanks,
Andruk

---

### Post by Andruk Tatum on 2007-12-22
*bump*

---

### Post by ronacc on 2007-12-22
try this , make a backup of your /etc/X11/xorg.conf    then edit your xorg.conf so that the device section reads like this

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection


note  you have to be root to edit the xorg.conf 
then kill x with  ctrl>alt>backspace  and install the driver from nvidia.com  (make sure you have the right one for your card and arch , the pkg1.run are 32bit and the pkg2.run are 64bit there is a list on the download page that tells you which driver works with what card.  if you are running a late release of ubuntu with "failsafe x" you will have to disable restricted manager or it will conflict . there are several threads that tell how to do that . after you install the driver just type startx  and you should be back at your desktop.  if it crashes you can just cd to /etc/x11/ and rename the backup to xorg.conf

---

### Post by Andruk Tatum on 2008-01-26
That, unfortunately, did not work.  I got a "no screens found" error and X wouldn't start.
Any other ideas?

Update: Installed with envy, and it loaded GNOME so far as the bug listed here on Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/146954](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/146954)

However, eventually the system did stop responding and I was forced to d a hard reboot (and no, not even ctrl+alt+F1, etc worked, it was frozen).

---

### Post by cmahlke on 2008-01-26
I tried to nstall the drivers for the 7600 and I still could not enable the video card.  I tried many different routes, including Envy.  I downgraded to a nvidia 6500 and it works perfect and was able to get the 3D going and everything. Maybe the available drivers (restricted and open-source) do not properly work yet?

---

