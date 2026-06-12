---
title: "MATE 1.6.0 Getting rid of Trash, Computer and Home desktop icons"
date: 2013-09-26
forum: Desktop Environments
---

### Post by suomalainen on 2013-09-26
Ubunteros,

I installed 12.04lts and then mate 1.6.0 as my desktop environment.

When Mate desktop appears first time there are three icons on desktop I can live without. EG home, computer and trash.

I tried using the "Configuration Editor" to remove them but the problem is the directory /apps/caja/desktop/ doesn't appear to exist. In this case there is no Caja/desktop.....

If anyone has the answer that would be great!

I'd like to ask not to receive comments regarding sticking with unity and hijacking this thread onto another subject matter.

Thank you!

---

### Post by tgalati4 on 2013-09-26
These commands seem to work in Linux Mint Mate 14 (based on 12.10) which uses Mate 1.4:

```


mateconftool-2 --type boolean --set /apps/caja/desktop/computer_icon_visible false

mateconftool-2 --type boolean --set /apps/caja/desktop/home_icon_visible false    

mateconftool-2 --type boolean --set /apps/caja/desktop/trash_icon_visible false

```

And you really should be using Unity.  (But I like Mate.)

---

### Post by suomalainen on 2013-09-27
This doesn't work because this MATE tool no longer exists.

Any other ideas?

---

### Post by buzzingrobot on 2013-09-27
> **suomalainen said:**
> This doesn't work because this MATE tool no longer exists.

Any other ideas?

The dconf editor replaced mate-conf in the 1.6 release.  Install "dconf-tools" if it isn't already there.  You should find "Dconf editor" in the System Tools menu.

Once launched, click on "org" in the left panel, then "mate", then "caja", and, finally, "desktop" (org->mate->caja->desktop).  On the right you will see checkboxes to toggle the visibility of the icons.

---

### Post by suomalainen on 2013-09-27
Thank you very much. Worked!!!!

---

### Post by egeezer on 2013-11-16
Thanks from me, too, buzzingrobot, because that also works in MATE on top of Ubuntu 13.04!

---

