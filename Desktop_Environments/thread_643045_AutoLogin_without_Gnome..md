---
title: "AutoLogin without Gnome."
date: 2007-12-17
forum: Desktop Environments
---

### Post by Mr. Electric Wizard on 2007-12-17
Hey Guys,
I know this has been probably been asked a thousand times already but I couldn't find a specific answer to my query.

I am currently running ubuntu (alternate install) with ICEwm as the desktop environment.
I have not picked out a login manager as of yet.
I am seeing lots of references to setting up AutoLogin in the System menu of Gnome, but no idea where you can do this without using Gnome.
Supposedly GDM has this functionality independeant of Gnome.
If I install GDM to open ICEwm, will I be able to put a username into a conf file somewhere in GDM to achieve this?

Also, after the autologin is working I need to run a script to start a virtual machine.
One thing at a time though, AutoLogin is the first step!

Thanks in Advance.

---

### Post by Mr. Electric Wizard on 2007-12-17
BTW, I don't think VMWare has to be run as root, so the autologin will be run for a very low level account (not root).

---

### Post by Mr. Electric Wizard on 2007-12-17
I got this from another forum.  Should this work?

```
kdesu gdmsetup
```

---

### Post by mali2297 on 2007-12-17
If you install gdm, you will be able to choose IceWM via the Session menu at login. 


> **Mr. Electric Wizard said:**
> I got this from another forum.  Should this work?

```
kdesu gdmsetup
```

Yes, but why do you want to use kdesu?
An alternative is to use gksu:
```

gksu gdmsetup

```

---

