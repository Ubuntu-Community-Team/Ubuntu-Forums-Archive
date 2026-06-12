---
title: "No gui after install. installer skips stuff?"
date: 2005-11-12
forum: Desktop Environments
---

### Post by Cannedbread on 2005-11-12
I just built a laptop especially for breezy, i got impatient and installed the breezy  RC1. it worked for a while but i did alot of crazy crap to it with drivers and stuff. 

well now i formatted and was going to reinstall with breezy stable.

instead of putting a cd drive in my computer i used that space for an extra battery, so i install through a netboot image.

every thing goes fine untile the installer gets to the point where it wants to reboot to install some packages and complete the installation.

the blue screen comes up that says, "downloading packages. 0 of 870" then the bar jumps from 0% to 100%, then the machine goes to a text based login prompt.

i can login fine but nothing works. after reading through this forum a bunch, here is a list of the commands i have tried.

ctrl+alt+f7
-does nothing

startx 
-command not found

/var/log/Xorg.0.log
-File not found

sudo vi /var/log/Xorg.0.log
-it creates a new file

sudo dpkg-reconfigure xserver-xorg
-Package is not installed

run /etc/X11/xorgcfg
-no such file or directory

sudo xorgcfg
-command not found

sudo apt-get update
-causes a whole bunch of errors, and then says "you may want to run apt-get update to fix this"

apt-get install X-window*
-package not found

sudo apt-get install xserver-xorg
-package not found

sudo dpkg --configure -a
-does nothing and doesnt affect any of the other commands

I am now out of ideas, ive tried the install like a bunch of times choosing different mirrors and it doesnt make any difference, the RC1 netboot installer had no issues. let me know what you think.

---

### Post by Ampersand on 2005-11-12
It sounds like the network might not be correctly configured. If you type 
```
ifconfig
``` does it come up with something sensible looking? Also, were you asked to enter the address of the DNS at any point during the setup?

---

### Post by Cannedbread on 2005-11-13
Well i figured it out.

at the beginning of the installer it asks me if i want to use my ethernet NIC or my Centrino WIFI to do the downloading. i chose WIFI so i could go sit on the couch with it while it installs. 

after the installer reboots the computer to install more packages, the wifi card doesnt automatically configure itself and so the packages cant be downloaded.

the screwey thing about it is that it does not throw an error or provide any kind of indication that something has gone wrong. perhaps this is something for bugzilla?

---

