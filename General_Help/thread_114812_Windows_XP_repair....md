---
title: "Windows XP repair..."
date: 2006-01-09
forum: General Help
---

### Post by shaj on 2006-01-09
ok guys I need help...

I need to perform a WinXP repair installation. Is that gonna overwrite the MBR? If yes, How do I get back my present Grub menu after I finish the repair install?

---

### Post by jasay on 2006-01-09
Take a look at the [wiki.]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub")  This seems applicable.

---

### Post by towsonu2003 on 2006-01-09
wow, that wiki is a mess (too complicated)... check out "recovering grub" in your local help documentation (System>Help>ubuntu guide) or here [http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation](http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation)

edit: just added ubuntuguide link to the beginning of that messed up wiki link.

---

### Post by Ocxic on 2006-01-09
YES, a WinXP repair installation WILL rewrite your MBR and you will prolly lose grub if it's installed onto the harddrive with windows.

---

### Post by jasay on 2006-01-10
Wow towsonu2003, that is a mess.  Guess I should have read more than the first paragraph or so explaining what the article was supposed to be about.  :oops: :oops: :oops:
Thanks for better documentation.

---

### Post by devnulljp on 2006-01-10
So, try doing the xp repair. Then boot from a linux boot disk (cd, floppy, ubuntu live cd, damn small linux, knoppix, whatever...) and mount your original linux partition somewhere (doesn't really matter where) and chroot it.

(example, with linux root partition on /dev/hda3 -- change accordingly, use fdisk to find out your partition table if not sure)

```
~$ mount /dev/hda3 /tmp 
~$ chroot /tmp

```

Then you can repair your grub from there like this.
```

~$ grub
Probing devices to guess BIOS drives. This may take a long time.
grub> root (hd0,2)
grub> setup (hd0)
grub> quit
```

Then, when you reboot, your old grub should be back the way it was.
* If you're not sure about partition locations, try this instead of root (hd0,2)
```
find /boot/grub/stage1
```

and then the** root (hdX,Y)** command with the correct parameters.

[QUOTE=Ocxic]YES, a WinXP repair installation WILL rewrite your MBR and you will prolly lose grub if it's installed onto the harddrive with windows.[/QUOTE]

---

