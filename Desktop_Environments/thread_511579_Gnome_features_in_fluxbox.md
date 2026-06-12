---
title: "Gnome features in fluxbox"
date: 2007-07-28
forum: Desktop Environments
---

### Post by WetWired on 2007-07-28
I was wondering if this was possible. I love gnome simply for it's ability to make things easier. I like how when I plug a thumb drive or camera into a USB port, it recognises it, mounts it, etc. Is there a way to make things like that happen in fluxbox as well?

---

### Post by aysiu on 2007-07-28
If you have Gnome installed (but aren't using it), add the command ```
gnome-volume-manager
``` to Fluxbox's startup file.

---

### Post by kerry_s on 2007-07-28
sudo apt-get install ivman

---

### Post by ugm6hr on 2007-07-28
> **WetWired said:**
> I was wondering if this was possible. I love gnome simply for it's ability to make things easier. I like how when I plug a thumb drive or camera into a USB port, it recognises it, mounts it, etc. Is there a way to make things like that happen in fluxbox as well?

I think you could use Thunar as a File Manager - it has a built-in Volume Manager (default plugin).  At least it does in XFCE.

---

### Post by WetWired on 2007-07-28
The volume manager controls all of that? Maybe this is a stupid question, but what does the volume manager have to do with detecting and mounting a USB camera / drive?

---

### Post by arch stanton on 2007-07-28
> **WetWired said:**
> The volume manager controls all of that? Maybe this is a stupid question, but what does the volume manager have to do with detecting and mounting a USB camera / drive?

Going out on a limb here but .. 'cause the the camera /drive is a storage volume and the manager manages it  :)

---

### Post by aysiu on 2007-07-28
> **ugm6hr said:**
> I think you could use Thunar as a File Manager - it has a built-in Volume Manager (default plugin).  At least it does in XFCE. Thunar alone won't do it. You also have to install the *thunar-volman-plugin* package.

---

