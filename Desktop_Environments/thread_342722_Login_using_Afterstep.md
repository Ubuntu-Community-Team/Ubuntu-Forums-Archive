---
title: "Login using Afterstep?"
date: 2007-01-20
forum: Desktop Environments
---

### Post by Ianna Atreides on 2007-01-20
I would like to make Afterstep my default window manager.  Having read the 

help files, I get the impression that logging in to Ubuntu is a function that 

is handled by Gnome (or KDE).  Is it possible to log in to Ubuntu using 

Afterstep as my default window manager, and if it is, what should I 

reconfigure in order to make this possible?


                                                  Thank You.

---

### Post by taurus on 2007-01-20
Do you currently have Gnome or KDE running on your machine?  If you have Gnome, then you are using gdm login screen and if you are using KDE, then it's kdm.  Look at the bottom left corner.  From there, you can choose which window manager you want to use.  When you pick AfterStep, it will ask you if you want to make it your default.  Pick yes and you don't have to choose it again.  It will log you into AfterStep after you enter your username and password from then on.

---

### Post by Ianna Atreides on 2007-01-20
I use Gnome.  Thank you for your advice about how to choose window manager.  Perhaps you can help me with something a bit more difficult (at least I think it may be :-)).

I would like to change the default boot runlevel, so that the X server does not start automatically.  I don't want it to start until the command "startx" is given.  This would make the entire screen a bash terminal at first, until the X server is started (If I remember correctly, this can be accomplished by changing the default runlevel in /etc/inittab to "3").

What worries me is whether I will be able to log on to Ubuntu at all if I do this.  I get the impression that Gnome of KDE must be running in order to be able to log on at all.

Is it possible to change the runlevel so that ubuntu boots without automatically starting X, and, if it is, how should I go about to make these changes without getting into trouble?

                                                   Thank You.

---

### Post by taurus on 2007-01-20
You don't have to change the run level in /etc/inittab.  You just have to remove gdm (and reinstall it again if you need it to boot int ogdm GUI login screen) and it will boot into a console.

```
sudo aptitude remove gdm
```
Reboot and see what happens.

---

### Post by dominator22 on 2007-07-24
Ubuntu doesn't use /etc/inittab .  Startup scripts are located in /etc/init.d/ and symlinked in /etc/rc#.d/  (#=runlevel #)  where they are being started/stopped depending on the runlevel.  See /etc/init.d/README and /etc/rc2.d/README for details.  

To set AfterStep as your default GUI - very wise choice ;) - replace the text in ~/.xinitrc to: 
```
#!/bin/sh
exec /usr/bin/afterstep
```

---

