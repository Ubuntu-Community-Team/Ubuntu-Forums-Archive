---
title: "Bootsplash Problem: &quot;Failed to load splash image...&quot;"
date: 2007-08-13
forum: Desktop Effects &amp; Customization
---

### Post by skibum1981 on 2007-08-13
I'm running Ubuntu with Gnome and I have been able to customize just about everything with no (well, little) problem.  However, I recently tried to customize my grub splash screen.  When I restart my system, just before the OS Boot selection screen, the following message appears:

"Failed to load splash image sdb1(0)/boot/grub/blubuntu.xpm.gz" and then waits for user input to continue, after which point the normal OS selection screen (no background/splash) appears and everything boots as normal.

The file blubuntu.xpm.gz is indeed in the directory.  I can open up the .gz and view the .xpm image just fine.  I downloaded the file from Gnome-look, so I figure it's been setup properly.  I have verified that I am indeed looking at the correct drive (I have 2 of them) by looking at the task manager.

Can anyone help me out here?  Help is much appreciated....  Thanks

---

### Post by skibum1981 on 2007-08-13
bump

---

### Post by skibum1981 on 2007-08-20
Bueler?

---

### Post by rsambuca on 2007-08-20
Post your /boot/grub/menu.lst file.  I am guessing that you have the splashimage= pointing to the wrong place.

---

