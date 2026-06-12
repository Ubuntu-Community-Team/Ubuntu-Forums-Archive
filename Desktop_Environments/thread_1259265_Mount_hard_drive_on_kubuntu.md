---
title: "Mount hard drive on kubuntu"
date: 2009-09-06
forum: Desktop Environments
---

### Post by MadnessRed on 2009-09-06
Hi, I want to know how I can mount my partition on KDE. In gnome I simple click on places and then on the partition and it mounts it. How do I do this in KDE? ATM I have to run nautilus as go to computer and open it there. Then I can browse it normally using dolphin.

I would like to know if there is a command line thing I can do which I can add to a shortcut in quick launch of something like that.

Also the fstab methods don't work on my computer. They stop the hard drive from being recognised as a hard drive in the Computer Place and it simply becomes a folder. I Don't want it mounting permanently or anything, I just want to be able to mount it like I do in GNome.

Many thanks

Anthony

---

### Post by simonyee on 2009-09-06
> **MadnessRed said:**
> Hi, I want to know how I can mount my partition on KDE. In gnome I simple click on places and then on the partition and it mounts it. How do I do this in KDE? ATM I have to run nautilus as go to computer and open it there. Then I can browse it normally using dolphin.

I would like to know if there is a command line thing I can do which I can add to a shortcut in quick launch of something like that.

Also the fstab methods don't work on my computer. They stop the hard drive from being recognised as a hard drive in the Computer Place and it simply becomes a folder. I Don't want it mounting permanently or anything, I just want to be able to mount it like I do in GNome.

Many thanks

Anthony

Hi,
It seems to happen when using ubuntu and add in KDE.
But with the Kubuntu there is no such problem and it is working properly.

How come ?
Thanks

---

### Post by MadnessRed on 2009-09-06
what do you mean it seems to happen when kde is installed onto gnome. I can mount fine using nautilus. But I would like a way to mount using Dolphin.

---

### Post by MadnessRed on 2009-09-08
bump

---

### Post by lykwydchykyn on 2009-09-08
Are we talking about a removable drive like a USB device, or a partition on a fixed disk?

Have you got the removable devices plasmoid on your panel?

---

### Post by MadnessRed on 2009-09-08
It is a partition on a permanent internal hard drive.

---

### Post by krazyd on 2009-09-08
It doesn't show up in the Places panel in the left of a Dolphin window?

---

### Post by lykwydchykyn on 2009-09-08
Do you not have a "places" menu in dolphin?  Or does the partition just not appear there?

Can you post your fstab file?

EDIT: I ask this because my dolphin on my home desktop (which has extra non-mounted fixed-disk partitions) has a "places" menu which lists the unmounted HDD partitions.  You can toggle it under "view=>panels" or by hitting F9.

---

### Post by MadnessRed on 2009-09-10
> **lykwydchykyn said:**
> Do you not have a "places" menu in dolphin?  Or does the partition just not appear there?

Can you post your fstab file?

EDIT: I ask this because my dolphin on my home desktop (which has extra non-mounted fixed-disk partitions) has a "places" menu which lists the unmounted HDD partitions.  You can toggle it under "view=>panels" or by hitting F9.

ok, found it, many thanks, looks like what I want. However, is it possible to have a link to my "DATA" partition on the desktop where when I double click its mounts it or opens it?

---

