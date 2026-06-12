---
title: "obvious way to boot to console? No gdm"
date: 2005-12-25
forum: Desktop Environments
---

### Post by bunutu on 2005-12-25
Is there some way to disable gdm, so that i can easily log in to console and (re)start Xorg when Xorg is broken.  Like when testing new DRI drivers for my savage card?

I'm not too familiar with ubuntu, just trying it out.  Before I start wading through initscripts and other arcana in /etc, I thought I'd ask if I'm missing something obvious like a gnome preference panel that will let me do this.

---

### Post by Ampersand on 2005-12-25
to get to a console, you can press Ctrl, Alt and F1 (or F2, F3, F4, F5 or F6). You can then control GDM using the /etc/init.d/gdm script using the commands
```

sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
sudo /etc/init.d/gdm restart

```
to stop, start or restart the display manager. You can also restart X by pressing Ctrl, Alt and Backspace.

---

### Post by shadesfox on 2005-12-25
In GRUB there is an option called Recovery Mode.  I think that will drop you into the console.

---

