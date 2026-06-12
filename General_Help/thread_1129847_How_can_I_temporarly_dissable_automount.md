---
title: "How can I temporarly dissable automount?"
date: 2009-04-19
forum: General Help
---

### Post by lavinog on 2009-04-19
I have a crashed hard drive that I am trying to recover info from.
It is external and it is not mountable because of the corruption. Ubuntu (Jaunty) attempts to mount it, causing the drive to be busy for a couple of mins. I can't start using dd_rescue until the mount procedure times out.

Is there a way to disable the auto mount feature, and turn it back on when done?
Or is there a way to ignore drives with a specific label or uuid?

---

### Post by Vadi on 2009-04-19
Either this command in the terminal:

> gconftool-2 --type bool --set /apps/nautilus/preferences/media_automount false

Or install the *[gnome-volume-manager]("apt:gnome-volume-manager")*, and in system - preferences - removable drives and media, poke about some.

If you want fine-grained control though, I think editing fstab will do it - I'm afraid I don't know any graphical tools for it, but you can search about the net: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by lavinog on 2009-04-19
Thanks for the reply.
I'm installing gnome-volume-manager now, but I think the gconftool command will be what I need.

---

