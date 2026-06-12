---
title: "what does ubuntu/kubuntu use for automounting?,menu font size in xine-ui?"
date: 2005-07-03
forum: Desktop Environments
---

### Post by ganja_guru on 2005-07-03
i use arch and kubuntu, and i find that ubuntu's mounting system is much better than what i use for arch linux(ivman)...can someone please tell me what ubuntu/kubuntu uses for automounting? is it in the kernel or userspace..

ive also found that xine in ubuntu has much better looking menu's than xine in arch linux..meaning smaller more refined fonts..is anyone aware where the config file for xine-ui to set the menu font size is?


thanks for your time..ubuntu rocks..!

---

### Post by varunus on 2005-07-03
Ubuntu uses the gnome-volume-manager (which relies on the freedesktop HAL) to automount disks.  I think the xine font preferences are in the file .gtkrc-1.2-gnome2 in your home folder (note the '.' and the beginning of the file name).

---

### Post by ganja_guru on 2005-07-03
that file contains:


# Autowritten by gnome-settings-daemon. Do not edit

include "/root/.gtkrc.mine"


.gtkrc.mine doesnt exist on my system..

does kubuntu also use the gnome-volume-manager?

---

### Post by ganja_guru on 2005-07-04
anyone?

---

### Post by varunus on 2005-07-07
I think you have to create .gtkrc.mine, I'm not sure of the format for fonts, but there's a font howto in the "tips and tricks" section, I think.

I'm not sure what Kubuntu uses...I remember KDE having some sort of automounting utility, and I know gnome-volume-manager does work under KDE (i've used it there before).

---

