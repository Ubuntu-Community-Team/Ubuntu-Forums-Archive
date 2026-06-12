---
title: "change screen resolution"
date: 2008-12-09
forum: General Help
---

### Post by monkeyking on 2008-12-09
Hi,
I tried to change the resolution using

menu->system->prefs->screen resolution,
which links to gnome-display-properties.

Now the system will boot up to graphic login screen,
but the screen becomes garpled or blacks out,
after I try to login.

Then I wanted to change my /etc/X11/xorg.conf as I have done in previous versions of linux.

But the xorg.conf doesn't contain anything with resolutions in it.
Actually, it only contains a device, motnitor and a screen section,
around 12 lines.

So where did all the x11 settings go,
and how do I undo the gnome-display-properties.

thanks in advance

---

### Post by mk1w86 on 2008-12-09
Ubuntu now auto probes the monitor and video hardware so the only configuration in xorg.conf is to tell it to auto probe.

---

### Post by monkeyking on 2008-12-09
Hmm, nice to know,
but how do I get my computer back.

---

