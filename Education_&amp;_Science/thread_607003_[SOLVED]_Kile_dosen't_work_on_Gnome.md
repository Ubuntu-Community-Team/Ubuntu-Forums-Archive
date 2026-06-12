---
title: "[SOLVED] Kile dosen't work on Gnome"
date: 2007-11-08
forum: Education &amp; Science
---

### Post by PacoCrespo on 2007-11-08
Hi, I have just installed without problems Kile but when I try to run it obtain the following error:

Could not read the network connection list
/home/elisa/.DCOPserver_elisa_laptop_0

Please check that the "dcopserver" program is running.

Do I have to move to KDE desktop????

thanks in advance

---

### Post by WebDrake on 2007-11-09
There should be no problems running Kile under GNOME.  I'm sorry, but I don't have any clue why you should get that bug---hope others can help.

You say you "installed without problems".... I take it you did things the normal way via the Ubuntu repositories?

---

### Post by earlycj5 on 2007-11-09
What WebDrake said, there should be no issues with it.

I've used Kile, Rkward, Quanta+ and other KDE apps with e17 extensively.

Using apt to check for unresolved dependencies would be my first step.

---

### Post by kleeman on 2007-11-09
Sounds like a permissions or ownership issue for some of your kde system files. Try this

sudo chown -R elisa:elisa /home/elisa

WARNING: I am assuming that your username is elisa. If it is not then substitute the real name for elisa everywhere above....

---

### Post by der_vegi on 2007-11-10
Maybe installing and running kcontrol helps? I think this creates some KDE-settings.
I am also running Kile right now, without problems. There is a process 'dcopserver [kdeinit] --n' running in the background...

---

### Post by PacoCrespo on 2007-11-13
I've installed KDE and now it's works¡¡¡

thank you all¡¡

---

### Post by leorolla on 2009-12-01
Did you try kleeman's solution?

```

sudo chown -R $USERNAME:$USERNAME $HOME/.kde

```

It should suffice.

---

