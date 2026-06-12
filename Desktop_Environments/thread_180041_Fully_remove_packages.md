---
title: "Fully remove packages"
date: 2006-05-21
forum: Desktop Environments
---

### Post by SB-X on 2006-05-21
I installed gcompris just to see what it does. After removing it and all associated packages (even using dpkg purge), I still have some files left behind on the system.
> 
/var/cache/apt/archives/gcompris-data_6.5.3-2+7.0.2ubuntu1_all.deb
/var/cache/apt/archives/libgcompris-1-0_6.5.3-2+7.0.2ubuntu1_i386.deb
/var/cache/apt/archives/gcompris_6.5.3-2+7.0.2ubuntu1_i386.deb
/var/cache/apt/archives/gcompris-sound-en_6.5.3-2+7.0.2ubuntu1_all.deb
/usr/share/gnome-app-install/icons/gcompris-edit.png
/usr/share/gnome-app-install/icons/gcompris.png
/usr/share/gnome-app-install/gcompris-edit.desktop
/usr/share/gnome-app-install/gcompris.desktop
/usr/share/locale-langpack/en_GB/LC_MESSAGES/gcompris.mo
/usr/share/locale-langpack/en_CA/LC_MESSAGES/gcompris.mo
/home/sbx/.local/share/applications/gcompris.desktop
/home/sbx/.local/share/applications/gcompris-edit.desktop

These were found with 'locate gcompris', so I don't know what all else it left. Is there a way to automatically remove everything? (I've already deleted the files under /home and /var/cache/apt/archives)

I'm a new user of Ubuntu and Debian-based package management.

---

### Post by Fass on 2006-05-21
The reason those weren't removed is probably because they weren't installed with the package. Also, the ones in /var/cache/apt/archives/ are the packages themselves that synaptic or apt downloaded. They won't be removed unless you tell apt to remove them.

---

### Post by SB-X on 2006-05-21
I thought it still needed to be uninstalled because after removing gcompris from the "Add Progams" tool, it was still in the Applications menu. (I know you can hide it.)
I just reinstalled the package and uninstalled again to try to reproduce this. It seems that you have to manually remove "gcompris-data" which I must have forgotten to do before looking at the Applications menu again. "Add Programs" doesn't list it.

Thanks anyway, and sorry to waste your time.

---

