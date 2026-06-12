---
title: "[SOLVED] Classical Booting screen in UBUNTU"
date: 2008-08-05
forum: Desktop Environments
---

### Post by Vishal Agarwal on 2008-08-05
Instead of seeing the default UBUNTU booting screen, I want to see the classical booting screen, where I can see the [COLOR="Green"][OK][/COLOR] (type of )report for all the activities. How is it possible.And after that it should reach to the default UBUNTU login screen.

---

### Post by mcduck on 2008-08-05
Edit the /boot/grub/menu.lst file, and remove the "splash" from the kernel boot line.

Then remove the same "splash" from the defoptions line as well, to make sure your change will stay even thugh kernel updates.

You won't get the nice green [ok], it will be in black&white. Enabling the colored messages is possible, although I haven't done it since 6.06 so I don't really remember how to do it any more..

---

### Post by Vishal Agarwal on 2008-08-05
I copied that first line from booting menu and now i had both graphical and black screen menu during booting.

---

