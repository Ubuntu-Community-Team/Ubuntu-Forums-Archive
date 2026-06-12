---
title: "Desktop background goes black when I click on Places"
date: 2010-01-11
forum: Desktop Environments
---

### Post by Gunnercw02 on 2010-01-11
Hello to all,

I've got an unusual problem I think? When I click on the "Places" tab in the upper panel my desktop background turns black and i cannot change it back without rebooting.  It only happens with this one tab, everything else work correctly, additionally I have to click whatever I'm trying to open music - pictures - etc. I have to click it twice to get it to open.  Another thing is when i open my picture folder none of the thumbnails show the pics it only shows a "gear looking icon". I did open nautilus once trying to get Sbackup to work because I had no permission to open the folders.  I removed it and I'm using Luckybackup which I really like so far.

Any help is greatly appreciated.

Thanks,
Bill

---

### Post by pavi_elex on 2011-11-04
/etc/init.d/gdm stop
and install
sudo apt-get install gdm
sudo apt-get install ubuntu-desktop
or
sudo apt-get install gnome-desktop-environment gdm x-window-system-core desktop-base
or
Try to fix broken packages in recovery mode.
or
upgrade your ubuntu version.

---

