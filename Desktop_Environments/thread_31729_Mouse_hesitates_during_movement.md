---
title: "Mouse hesitates during movement"
date: 2005-05-04
forum: Desktop Environments
---

### Post by georgec on 2005-05-04
I have a Dell Inspiron 8100 that has a touchpad and the keyboard stick mouse.  Regardless of which mouse I use or even a USB optical mouse, the movement will pause a fraction of a second during my moving the mouse pointer.  It's as if there were heavy processor activity taking place.

Does anyone else experience this?  I also experience this in gnome.  Other distro's do not do this on my laptop.

Thanks

---

### Post by elsewhere on 2005-05-04
I've got the same laptop and had the same problem, you probably have a number of messages in your kernel log referring to psmouse.c losing synch etc.  Try disabling the powernowd service and see if that helps, I know it solved the problem for me.  Something to do with acpi / irq conflicts between powernowd and the touch pad.  

Of course, I've lost cpu frequency scaling now but that's a much smaller annoyance and there are alternatives to powernowd.

FWIW, I ran into the exact same issue when I was using FC3 after I upgraded from their last 2.6.10 kernel to 2.6.11, had never seen it prior to that.  Strange since FC3 doesn't use powernowd, must be the action and not the application.

Anyways, hope this helps !

Cheers,
KV

---

### Post by georgec on 2005-05-04
Thanks elsewhere.  Will I have to perform this on each reboot?

---

### Post by elsewhere on 2005-05-05
No, if you determine that powernowd is causing your problem as well, you can just disable the service from starting at boot.  It can be permanently disabled manually, or with a utility like sysv-rc-conf (my personal preference).

Cheers,
KV

---

