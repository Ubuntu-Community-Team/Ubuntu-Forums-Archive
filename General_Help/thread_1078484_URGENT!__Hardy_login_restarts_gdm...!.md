---
title: "URGENT!  Hardy login restarts gdm...?!"
date: 2009-02-23
forum: General Help
---

### Post by echoes73 on 2009-02-23
Hello, I'm a college student that uses Linux for computing courses that I take (been using Linux for years).  Anyways I stay at a relatives during the week and I installed Ubuntu 8.04 along side XP on their desktop.  When I boot into ubuntu for one the splash screen does not work, then when the gdm opens and I login the screen goes to the pale orange as usual and then to black, after that the gdm restarts.  No matter how many times I login the loop continues.  I'm guessing it has to do with the ATI drivers not being installed yet but...  This desktop has a wireless connection and I have no wired connection available so if it is the drivers that are messing with me how do I go about fixing such a problem?  All help is appreciated greatly and I need an answer soon if possible.  Thank you...

---

### Post by spiderbatdad on 2009-02-23
not sure but there are a couple of bug reports:
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/130066](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/130066)
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/164039](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/164039)
In other words get access to a terminal with alt+f1 and stop gdm 
/etc/init.d/gdm stop
then startx, or try purging gdm and reintalling it...not sure how well the latter will go. If you can get running and connect to the wireless network, perhaps you can run update manager and solve all problems.

---

### Post by balaknair on 2009-02-23
You could try using safe graphics mode; if it really is the ATI drivers causing the trouble, that ought to enable you to log in and install the ATI drivers via the 'Hardware Drivers' utility in System menu--> Administration.

Alternatively, if safe mode doesn't work either, at the log-in screen, hit ctrl-alt-F1 to open a console, log in, and force VESA graphics mode via the command line. Here's how you can go about it(hint: write this down or take a print out, since you're going into command line territory)

1) When the screen comes up blank(with the errors etc.), press Control+Alt+F1, to get to a text console(no GUI). Then edit the video configuration file (/etc/X11/xorg.conf) using the command

sudo nano /etc/X11/xorg.conf

2) You'll see a file with # comments and immediately below that a section that says

Section "Device"
Identifier "Configured Video Device"
EndSection

3) Add a line after the identifier which forces the driver, Driver "vesa" so that the file looks like this.

Section "Device"
Identifier "Configured Video Device"
Driver "vesa"
EndSection

4) Save the file, by pressing Control+X, then Y, then press 'Enter'. Now press Control-Alt-F7 to return to the blank screen, then press Control+Alt+Backspace to restart the X server, and if all goes well, the X server will restart and you will have a barebones GUI which you can use to repair Ubuntu.


Hope this helps.

All the best.

---

