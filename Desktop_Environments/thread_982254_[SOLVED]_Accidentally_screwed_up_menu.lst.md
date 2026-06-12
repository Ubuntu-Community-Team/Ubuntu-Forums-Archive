---
title: "[SOLVED] Accidentally screwed up menu.lst"
date: 2008-11-14
forum: Desktop Environments
---

### Post by Cammy on 2008-11-14
Yes, I'm an idiot.  I was trying to add an option to my menu.lst file and I managed to screw it up.  So I copied a backup version over, BUT the backup does not seem to have the proper kernel I need.  So now when I boot up, my /home/user directory is missing.

Is there any way to get the correct entry into menu.lst, or have I lost everything?

---

### Post by aged hippy on 2008-11-14
If you look in /boot/grub you _may_ find a file named **menu.lst~** - which _may_ be the auto-backup of the one you altered.

If it is there, move the present one somewhere, and remove the **~** on the backup. :)

---

### Post by caljohnsmith on 2008-11-14
Just do:
```
sudo update-grub
```
and the new kernel should be added to your menu.lst, assuming your "groot" and "kopt" lines in your menu.lst are OK, among other things. If you have any problems with it though, let me know. Otherwise let me know how it goes. :)

---

### Post by aged hippy on 2008-11-14
> **caljohnsmith said:**
> Just do:
```
sudo update-grub
```
and the new kernel should be added to your menu.lst, assuming your "groot" and "kopt" lines in your menu.lst are OK, among other things. If you have any problems with it though, let me know. Otherwise let me know how it goes. :)

That's a handy one to know. :)

---

### Post by Cammy on 2008-11-14
Yes, QUITE useful!

I'm back in my proper kernel again!

---

### Post by caljohnsmith on 2008-11-14
> **Cammy said:**
> Yes, QUITE useful!

I'm back in my proper kernel again!
That's great news. You might want to backup your menu.lst to have a working copy in case something else happens:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup

```
Anyway, cheers and have fun. :)

---

