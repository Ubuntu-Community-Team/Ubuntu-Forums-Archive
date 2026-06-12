---
title: "Remove/disable GDM?"
date: 2010-03-24
forum: Desktop Environments
---

### Post by javyn999 on 2010-03-24
I'd like to have it to where when I boot up my computer and select Ubuntu from GRUB, for it to boot to command line and force users to login from there.

Is it safe to do a sudo-apt remove gdm, or is there a better way?

---

### Post by diesch on 2010-03-25
It should be enough to write something like
 ```
None
```
into [I]/etc/X11/default-display-manager
[/I]

---

### Post by thesenu on 2010-03-25
i think you can restart or disable it
[B]sudo /etc/init.d/gdm restart
[/B][B]sudo /etc/init.d/gdm stop

[/B]you can use install kde

---

### Post by javyn999 on 2010-03-25
Well I still want to keep and use GNOME.  I just don't want the login manager.  I don't understand, login managers serve such a simple function, but they are all so bloated.

I want it disabled, out of my RAM, period.  So I can just login from command line and start GNOME from there.

---

