---
title: "Use startx rather than GDM"
date: 2007-04-06
forum: Desktop Environments
---

### Post by musther on 2007-04-06
I have just set up an old machine running ubuntu.  I've decided to use openbox as my window manager, and now have no need for GDM.  What I want to set up for this machine is a boot straight to openbox without GDM.

I need to:
1 - Stop GDM from loading (should be easy with BUM - Boot Up Manager)
2 - Add 'startx' to a script somewhere to be called after login - but I don't know where
3 - Make the user log in automatically (as it does currently with GDM) - again, don't know how

So it's point 2 and 3 I'm having trouble with, can anyone help?

Thanks

---

### Post by kerry_s on 2007-04-06
Not a good idea, in ubuntu alot of things are tied together, gdm setup the session with out it you get a lot of quirkyness and unexpected bugs, you can setup gdm to just auto login and you will never see it unless you want to. You can add> 1 <to your boot line if you don't want to boot into gui.

gdm setup:

gksu gdmsetup


If just must do it the hard way-> [http://ubuntuforums.org/showthread.php?t=303319](http://ubuntuforums.org/showthread.php?t=303319)

---

### Post by musther on 2007-04-06
I'll leave GDM then, thanks for the advice.

---

### Post by tbroderick on 2007-04-06
Edit...didn't see kerry_s link. Mine is pretty much the same except using mingetty. FWIW, I haven't had any problems not using GDM.

---

### Post by kerry_s on 2007-04-06
> **musther said:**
> I'll leave GDM then, thanks for the advice.

As far as size goes i've gotten my system down to 500-->600mb with gdm, so if your worried about size you can trim else where to get to the size you want. In edgy it pretty safe to go with out gdm, but there is a lot of underlying quirks, you have to watch those logs they fill up quick with errors, some like .xsession-errors will just end with to much info error. I have gdm installed but haven't seen it for along time. I'm running a feisty-server+fluxbox install.

In feisty i really recommend having gdm.

---

### Post by musther on 2007-04-07
I'm not worried about disk space on this machine, just memory and CPU usage.

---

