---
title: "Can't log in to Gnome"
date: 2007-11-09
forum: Desktop Environments
---

### Post by drewcrumpton on 2007-11-09
Hi, I don't know if this is the right Forum to post this but I am very stuck.

I have used Linux a bit over 3 years ago so am nearly a beginner at this.

I have an ATI Radion graphics card which I installed using a link given through ATI's web site. After working through all the commands etc. I have managed to get the card working, however, when I log in using the gnome interface, the mouse pointer with the brown background appears for a bit, followed by the screen turning black. It did return to the log in screen again before a work colegue allowed Root to log in (Which acted the same way). Now it just stayes black and you can't even use CTRL-ALT-F? to change to a txt based screen (Before you try to log on you can). If any one could point me in the right direction I would be very greatful.

Thanks

Drew

---

### Post by bcspratt on 2007-11-09
It sounds like your video configuration file (/etc/X11/xorg.conf) was accidentally mis-configured or corrupted which has happened to me a few times.  If so, fear not it can be fixed.  It happened to me the other day when I upgraded from Feisty Fawn to Gutsy Gibbon.  My Nvidia video card requires a special driver not included in Ubuntu, so when the kernel was upgraded I had to reinstall my video driver.  Installing the driver was easy but if you don't know how to do it, it is scary?
	Assuming your xorg.conf file is mis-configured, if X11 can't find the xorg.conf file then it should try to build you another one automatically at boot up.  To do that (safely) I would suggest the following:
* At the boot up menu choose recovery mode.
* Once you get to the command prompt, login as either your regular user ID.
* Command “cd /etc/X11” will get you to the correct folder.
* Command ls -la will list all the files in the directory.  You might take note if xorg.conf is missing or the time date stamp indicates that it was updated recently.
* Assuming xorg.conf is there, command “sudo mv  xorg.conf  xorg.conf.bkp” will rename your existing xorg.conf file.  Note: use “sudo mv  xorg.conf.bkp  xorg.conf” to put it back if this does not help.
* You can either restart your PC or use the command “startx” which will start X11 and should build you a new xorg.conf file.
	
	If you have a fancy video card then X11 might only give you basic functionality but you should be able to reinstall your ATI video driver and then things should be right as rain.

---

### Post by drewcrumpton on 2007-11-14
Ran through that, thanks but only get's me a little bit further. I now keep going back to the login screen.

---

