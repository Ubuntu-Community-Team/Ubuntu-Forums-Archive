---
title: "removing restore points from grub"
date: 2007-02-14
forum: Desktop Environments
---

### Post by larrybrazos on 2007-02-14
I was playing around with compiz and crashed my xserver.  I was able to get back in my choosing a different restore point from GRUB.  Now I want to remove the restore point that I know is corrupted.  How do I remove restore points from GRUB.

Also, how do I add a new restore point.  For example, I want to try my hand at compiz/beryl and would like to make a restore point on the GRUB menu before I start messing around.

Thanks.

---

### Post by larrybrazos on 2007-03-09
fixed this problem, if anyone else is confused . . .

first off, i did not break anything.  i updated my server install and the new kernal had a module issue when trying to find my graphics card.

second, if you loose your xserver for whatever reason when messing with your graphics driver, you can choose recovery mode from grub and use this method to get back in to your gui . . .

back up xorg.conf . . .

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

edit xorg.conf to use "vesa" drivers so you can get back in to your gui . . .

sudo nano /etc/X11/xorg.conf
find the device section and, if you have an nividia card you were working with, take out "nv" or "nvidia" and use "vesa" as your device driver.

this will let you back in to ubuntu with a gui and you can investigate your graphics issue.

as far as removing grub restore points, i read an awesome blog post on how to do this, and now i can't find it :(

just look in ubuntu forums for something like "edit grub boot options"

---

