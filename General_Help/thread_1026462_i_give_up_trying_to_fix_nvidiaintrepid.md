---
title: "i give up trying to fix nvidia/intrepid"
date: 2008-12-31
forum: General Help
---

### Post by jesse c on 2008-12-31
After spending more than 100 hours trying to get xserver going for my nvidia 9400gt graphics card ive given up.My hardware driver shows nvidia 177 driver enabled but no x server settings cant be solved.Question-if i just wait will some future intrepid update automatically fix this when the bugs get worked out or will i need to keep working with forums to fix this myself?

---

### Post by dexter on 2008-12-31
According to the documentation, 177 driver should support the 9400GT (see /usr/share/doc/nvidia-glx/README.txt.gz). 
Do you know what is causing the failure of the x server (see /var/log/Xorg.0.log)? 
Does it work with the nv driver?

---

### Post by jesse c on 2008-12-31
I do not know why the x srver wont work,all i know is the hardware driver says 177 is enabled but the x server settings says xconfig file not woking and the 'sudo nvidia-xconfig' command doesnt work to fix the problem

---

### Post by jesse c on 2008-12-31
Where do i get the nv driver? Its not listed in synaptic and some forums recommended envyng but i could only find envying-gtk which i tried anyway

---

### Post by ju2wheels on 2008-12-31
> **jesse c said:**
> Where do i get the nv driver? Its not listed in synaptic and some forums recommended envyng but i could only find envying-gtk which i tried anyway

Lets try fixing what you have first, could you post your /etc/X11/xorg.conf please.

---

### Post by cb951303 on 2008-12-31
did you try enabling NVIDIA drivers from System->Admin->Hardware Driver before messing with nvidia-xconfig, xorg.conf etc...?

---

### Post by 73ckn797 on 2008-12-31
> **cb951303 said:**
> did you try enabling NVIDIA drivers from System->Admin->Hardware Driver....?

This ought to be the first step in getting Nvidia to work. I have not had any Nvidia issues with 9600GS and the 177 (Recommended) driver. Running 8.10 64bit or 32bit.

---

### Post by OmnyDevi on 2008-12-31
Did you try installing Envy? I know my nvidia cards used to give me all kinds of hell. For a while, Envy was the only thing I could get to install the right driver. Awesome little app. Now it's my Nvidia software raid that I can't get to work....always something new to play with :D

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

The above link should take you to the envy page. Happy hunting :)

To get into at least some kind of graphical mode, edit (vi) as root the xorg.conf..I believe in /etc/X11/xorg.conf
Find the display driver and you will see the driver is "NV" or "NVIDIA". Change it to "VESA", hit esc, press : then type wq and hit enter. After that, startx and hit enter. Let me know the results please. :)

Dont expect a good resolution or anything, but it should be enough to get envy and get this thing rolling.

---

### Post by jesse c on 2008-12-31
sorry,im at work now so cant post my xorg conf output right now, but i did get my 177 package from synaptic and did enable it in 'hardware driver' and it is checked green and says it is enabled and also header says that my system has a propriatary driver in use but x server says x driver needs restarting but the 'sudo nvidia-xconfig' command does not fix the restart problem.
and i have not messed with my xconf settings since my last clean install

---

### Post by LowSky on 2008-12-31
once you install the driver you need to reboot the computer. Has that been  done?

You can also try booting into recovery mode from GRUB and using XFIX

---

### Post by jesse c on 2008-12-31
home from work. Lets see: yes i have rebooted the computer,yes i have gone to grub and did the fix x thing. But for the record my monitor has good resolution after it boots but it boots with a pop up window that tells me its starting in low graphics mode but it ends up looking pretty good yet i cant enable any extra visual effects in system/appearance cause it says graphics wont support extra effects and,like i posted there is no xserver settings in sys/administration although it is enabled in synaptic

---

### Post by dexter on 2009-01-01
Can you show us the content of your xorg.conf file? (/etc/X11/xorg.conf)

---

### Post by jesse c on 2009-01-01
ok but whats the command to bring up xorg file?
sorry reviewed older post and found command
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

jesse@jesse-desktop:~$

---

