---
title: "How Can I Restore Dual Boot Without Reinstalling Ubuntu?"
date: 2009-01-25
forum: General Help
---

### Post by ram2008 on 2009-01-25
****I'm planning to install Windows XP Pro over my XP Home installation which is dual booting with Ubuntu.  I imagine that the installation of XP Pro will wreck the dual boot (Grub).  I would like to know how to restore it after installing XP Pro without having to re-install Ubuntu.  Is that possible?  Thanks for your help.

---

### Post by dcstar on 2009-01-25
> **ram2008 said:**
> ****I'm planning to install Windows XP Pro over my XP Home installation which is dual booting with Ubuntu.  I imagine that the installation of XP Pro will wreck the dual boot (Grub).  I would like to know how to restore it after installing XP Pro without having to re-install Ubuntu.  Is that possible?  Thanks for your help.

Do a forum search for "reinstall restore grub" and it should return a detailed HOWTO (or 10....) - it isn't that difficult to restore.

---

### Post by ram2008 on 2009-01-28
I found the following directions and followed them but it did not restore Grub:

Code:
   sudo grub

Code:
   find /boot/grub/stage1

Code:
   root (hd2,0)  (These were my actual results.)

Code:
   setup (hd2,0)

Code:
   quit

I still have no grub menu when I boot.  Did I miss something?  Shouldn't grub be altering the MBR of hd0 (or hda1 my first hard drive)?

---

### Post by Boomhauer on 2009-01-28
how many hard drives do you have on your computer?  which one is ubuntu on and which one is vista on?

---

### Post by caljohnsmith on 2009-01-28
Can you set your BIOS to boot the sdc Ubuntu drive on start up? If so, how about doing:
```
sudo grub
grub> root (hd2,0)
grub> setup (hd2)
grub> quit
```
Reboot, set your BIOS to boot the sdc Ubuntu drive, and let me know how far you get. We can work from there if you want.

---

