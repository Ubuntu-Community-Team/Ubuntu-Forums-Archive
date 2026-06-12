---
title: "Formatting to dual boot xp and ubuntu"
date: 2009-04-05
forum: General Help
---

### Post by Cogsworth on 2009-04-05
Hi all.  Wasn't sure if this belonged in installation or general, seeing as how it mainly pertains to an issue with xp.  Oh well.

Basically, my problem is this:

I want to be able to dual boot xp and ubuntu.  However, whenever I pop in the disk to install windows xp, I make it all the way to the partition selection screen...and it freezes.  I know it's frozen, because it allows me to open the disk tray and remove the disk mid-install.

I had a feeling that the partitions were to blame, being formatted for use with ubuntu.  So I opened the partition manager and formatted the entire disk to fat32.  Still, the installation froze at the exact same screen.  I performed a fresh install of ubuntu 8.10, and here I am.

Note: When attempting to virtualbox xp, the install does not freeze until the formatting actually begins.

Note2: I've tried it with two different disks; the disk is not the problem.

Any assistance is greatly appreciated.  If further information about the problem is required, ask and ye shall receive.  Thanks!

---

### Post by Merk42 on 2009-04-05
Sounds more like a problem with Windows than Ubuntu.

I take it you're booting from the CD and have had experience in installing XP in such a way before?
What happens if you try making a partition in NTFS?

---

### Post by Cogsworth on 2009-04-05
It doesn't really help.  As soon as I get to the partition screen, it freezes completely; I can't move up or down to select the partitions.

---

### Post by Merk42 on 2009-04-05
My memory is a bit foggy, been so long since I installed XP from scratch...

I may be completely wrong, but I seem to remember something wonky with USB devices during a fresh XP install.

Is this your problem?
[http://computerhelpforum.org/forum/operating_systems/f13/keyboard_not_recognized_during_windows_xp_fresh_install/t20169.html#entry125500](http://computerhelpforum.org/forum/operating_systems/f13/keyboard_not_recognized_during_windows_xp_fresh_install/t20169.html#entry125500)

---

### Post by Cogsworth on 2009-04-05
> **Merk42 said:**
> My memory is a bit foggy, been so long since I installed XP from scratch...

I may be completely wrong, but I seem to remember something wonky with USB devices during a fresh XP install.

Is this your problem?
[http://computerhelpforum.org/forum/operating_systems/f13/keyboard_not_recognized_during_windows_xp_fresh_install/t20169.html#entry125500](http://computerhelpforum.org/forum/operating_systems/f13/keyboard_not_recognized_during_windows_xp_fresh_install/t20169.html#entry125500)

Oh man, I can't believe I forgot that!  I'm using a wireless keyboard that runs off of a usb slot #-o

I really think that may be the problem, let me try that.

---

### Post by majamba on 2009-04-05
simple partion setup
first one windows
second one linux
3 could be swap or logical

remember that when you install grub bootloader on linux partions so doesn't corrupt windows mbr

and just make the linux partion bootable

---

### Post by Cogsworth on 2009-04-05
Oh wow...the keyboard thing was the problem.  Thanks a lot guys...I feel kind of dumb now :p  But my problem is solved!  Thank you again.

---

