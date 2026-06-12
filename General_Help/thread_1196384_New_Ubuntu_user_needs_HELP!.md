---
title: "New Ubuntu user needs HELP!"
date: 2009-06-24
forum: General Help
---

### Post by politico34 on 2009-06-24
Hi, I'm a new Ubuntu user.
I have a PC set to dual boot XP media center edition and Ubuntu.
After a session of Ubuntu where I installed the driver for my D-Link DWL-G510 (Win 98 with ndiswrapper) and then I enabled compwiz and turned on a bunch of special effects.
Here is the problem:
When I boot Ubuntu it loads but sits on the blank desktop with the "hourglass" cursor forever and never actually loads. 
When I push the power button it says that file system and other important looking items are not responding. 
Cannot bring up terminal with crt+alt+f1 
Any help would be appreciated. 
thanks

---

### Post by philcamlin on 2009-06-24
dont know what your issue is but terminal is ctrl alt f2 :popcorn:

exit: oops i learned both work

---

### Post by ad_267 on 2009-06-24
Do you get to the login screen?

Can you get to another tty (Ctrl+Alt+F1 to F6, there's 6 of them) from there?

If so you could try adding another user with the command:
sudo adduser username

Then try logging in as that user. If that won't work you can boot into recovery mode from the boot menu and run that command to add a user.

---

### Post by politico34 on 2009-06-24
So if I could set up a new user account would that allow me to get into OS since the settings are at default or something?

---

### Post by ad_267 on 2009-06-24
> **politico34 said:**
> So if I could set up a new user account would that allow me to get into OS since the settings are at default or something?

Hopefully. If you can log in as another user it would indicate that it's only a problem with your account, and not a system wide issue. Then you could try removing any of your user configurations that could be at fault like your Compiz settings. If you create a new user and still can't log in as that user then it tells you the problem is something more serious.

---

