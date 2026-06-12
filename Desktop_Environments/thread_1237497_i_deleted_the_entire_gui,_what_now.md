---
title: "i deleted the entire gui, what now"
date: 2009-08-11
forum: Desktop Environments
---

### Post by thundaraptor on 2009-08-11
I have been trying to get big desktop to work with a dual head ati graphics card.  In doing so, I decided to uninstall via synaptec randr and when I executed this it pretty much uninstalled the entire system, jaunty 64.  Now I am booting directly to the command line.

Seriously, it is true I am an idiot and did this because I had previously installed a resolution switcher that I thought was conflicting with ATI catalyst controls but probably randr is a bigger deal, not that I would know.  Any ideas on how to restore the system?  I have hardy heron installed in another partition and the grub loade gives me lots of options so I am not totally out but I would like to make the reconfiguration of the system as easy as possible, if possible.

Thanks,  

TR

---

### Post by rainwalker on 2009-08-11
Can you reinstall whatever it was you uninstalled?

---

### Post by thundaraptor on 2009-08-11
I have no clue, i marked a program for complete uninstallation and it went through the entire system.  At this point I am backing up relevant information and getting to clean sweep.  I think the better question is how to completely uninstall a kernal and make the new install?

---

### Post by rainwalker on 2009-08-11
I know a history is kept somewhere, but I'm not sure how to get to it without being able to open Synaptic. You could try googling to figure out how to view the history from the command line, so you can figure out what you uninstalled :?

---

### Post by andrea000 on 2009-08-12
your booting in to the terminal right??? if so do a
sudo synaptic that will get you to the package manager
but with out knowing what you uninstalled i dont know
anymore to tell you

---

### Post by oldos2er on 2009-08-12
I think you'll find a log of package activity in /var/log/dpkg.log . You can open this file when you boot into recovery mode with the command
```
nano /var/log/dpkg.log
```
then hit Alt-/ to go to the end of the file. Hopefully from there you can see what commands you need to to reverse.

---

### Post by oldos2er on 2009-08-12
> **andrea000 said:**
> your booting in to the terminal right??? if so do a
sudo synaptic that will get you to the package manager
but with out knowing what you uninstalled i dont know
anymore to tell you

 Synaptic requires a GUI to run, and it doesn't sound like the OP has a GUI.

---

### Post by lisati on 2009-08-12
Something that might be worth a try at the command line is this:
```
sudo aptitude install ubuntu-desktop
```
If things are not too badly broken, this should get a gui back for you.

---

### Post by jacksaff on 2009-08-12
sudo aptitude install ubuntu-desktop

will install all of the packages required for a standard ubuntu install. 

When done you can exit and should reboot to the login screen.

All needed packages should be installed and all of your old config should still be there.

If this doesn't work then post back - you have probably installed a dodgy graphics driver.

---

### Post by 3rdalbum on 2009-08-12
lisati and jacksaff are correct. Follow their suggestion, but before you do:

```
sudo rm /etc/X11/xorg.conf
```

Just to make sure that when Xorg installs, it is installing completely fresh.

---

