---
title: "kde4 automount utf8"
date: 2008-07-31
forum: Desktop Environments
---

### Post by adichou on 2008-07-31
Hi all,


Since I googled this without any result I ask for your help. KDE4 fails to automount my USB pendrives with utf8 support. I can manage to do it by umounting then sudo mount -t vfat -o iocharset=utf8 /dev/sdb1 /mnt/usb, but then only root can access the pendrive. Is there something I could do to add the option iocharset=utf8 to automount config. I have no problem with KDE 3.5.9 and with Gnome.

Thanks very much for your help. I want to switch to KDE4 but can't beacause of this annoyance.:(

---

### Post by adichou on 2008-08-03
No clue anyone? Strange. The problem persists since the first betas of KDE4. Many people have reported it. No fix till now. All the distributions I tested got the same problem. I think it must be a kde4 problem and in the kde forums, no answer too!

---

### Post by bierholen on 2008-08-29
I would very much be interested in a solution for this as well.

---

### Post by vitorsouza on 2008-09-29
> **bierholen said:**
> I would very much be interested in a solution for this as well.

So would I. Looks like it's a bug:

[http://bugs.kde.org/show_bug.cgi?id=161588](http://bugs.kde.org/show_bug.cgi?id=161588)

People mention workarounds, but sounds like you have to get the source, patch and recompile and, frankly, I don't know how to go about it. If anyone know any workarounds, please post a mini-Howto?

Vitor

---

