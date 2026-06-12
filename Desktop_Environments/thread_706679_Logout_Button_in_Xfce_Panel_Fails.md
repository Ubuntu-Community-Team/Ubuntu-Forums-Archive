---
title: "Logout Button in Xfce Panel Fails"
date: 2008-02-24
forum: Desktop Environments
---

### Post by radiocognition on 2008-02-24
I recently installed xubuntu on an old laptop, and this is my first go around with xfce.  I am unsure exactly what happened, but during a session, xubuntu refused to reboot.  I was under the impression that one of the programs was crashing, so I did a hard reset and logged back into xubuntu.  Once I was logged in though, my panels were whacked up (they loaded but with the default xfce prefrences instead of the xubuntu settings).  I figured out that every time i shut off xfce, it saves my panel settings.  Perhaps the panel manager had crashed and rebooted with the xfce default, and when I rebooted my machine, my settings were overwritten.

Most disturbing of the changes to my panel was the failure of the "quit" button on the top panel.  No longer would it open up the quit xubuntu / logout Xfce dialogue, so there was no way to log out with the GUI.

I rebooted the machine and logged in under the account of another user.  This user still had the default xubuntu panel settings.  I copied the second user's ~/.config/xfce4/panel folder to the user with the goofed up panels.  Restarting xfce panels gave me the default Xubuntu panels, but the "quit" button *still* didn't work.  What is going on and is there a way to fix it without having to reinstall?

---

### Post by radiocognition on 2008-02-24
It just started working again . . . no particular reason . . . it just decided to work.  Very buggy indeed.

---

### Post by mathomas3 on 2008-05-29
i have the same problem?

but how does it get fixed?

---

### Post by atomkarinca on 2008-05-29
> **mathomas3 said:**
> i have the same problem?

but how does it get fixed?

If I remember correctly you have to install a package called xlock. Open up a terminal and  type:

```
sudo apt-get install xlock
```

---

