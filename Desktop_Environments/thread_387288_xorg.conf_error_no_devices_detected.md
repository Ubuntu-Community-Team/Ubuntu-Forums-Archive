---
title: "xorg.conf error: no devices detected"
date: 2007-03-18
forum: Desktop Environments
---

### Post by wess126 on 2007-03-18
Hi All,

I am having a slight problem with the X11. 
I am runnuing Ubuntu 6.06 (dapper drake on a dual boot Dell Optiplex GX620: ATI radeon X600 series graphics).

Yesterday I tried installing a 3D desktop and the enlightenment window manager on the above mentioned system. The 3D desktop failed as I couldnt connect to Beryl but I managed to get enlightenment installed using src and deb packages (Synaptic would not instal data and base package). Once this was done I rebooted and thats when my problems started. I basically lost all GUI and was left with the command line. After reading several threads on the net I ran 

$ dpkg-reconfigure xserver-xorg

This did not help at all until I chose the 'vesa' driver as opposed to the 'ati' one. When I then type

$ startx 

I get my GNOME desktop back, unfortunately their are new problems. Once into GNOME I get a message relating to the dbus power management system!! (have no idea what this is!!)

If I then reboot I get the standard Ubuntu login screen (which I didnt have before), this is good, only I enter my username and password and it just takes me back to the original login screen. If I boot into safemode I can start X11 up using 

$ startx

but am back to where I started with the dbus error and limited desktop applications.

So, I would like to know if I can reinstall the entire X11 system from the command line and thereby restore my system to its original self. Unfortunately I cannot include my xorg.conf and associated log file as I have'nt figured out how to mount a flashdisk from the command line.

Any help or comments would be greatly appreciated and thanking you in advance for your time.

regards,
WEs

---

