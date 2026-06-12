---
title: "ntfs vfat mount option (utf8) not working with xfce"
date: 2008-07-24
forum: Desktop Environments
---

### Post by smarf on 2008-07-24
Hi there,

using XUbuntu since one happy :) year now, I upgraded my well working 7.10 installation to XUbuntu 8.04. Many things changed, most problems are solved thanks to this excellent forum. :)

Two problems remain after hours and hours of googleing and searching:
- After plug-in of a USB-harddisk, the "mount" option in the context menu of the correctly appearing icon on the desktop results in a mounted partition with wrong (ie.: missing) utf8-setting. I tried several things like gconftool, changing hal-preferences and hal-policies, but everything without effect. I don't want to add an entry for each partition in fstab, I want to change all default mount-activities (vfat, ntfs). In 7.10, a changed locale-setting was the key, not so in 8.04. Which is the correct way to enable utf8 for all mounted partitions?
- I don't want to eject the partition of the USB-harddisk (there are several partitions on one disk), I want to unmount them. Where can I configure this? In 7.10 there was an unmount-option in the context menu, not so in 8.04.

Everything is working well on the command line interface, but not through the graphical user interface. Which configuration files do I have to change?

Thank you in advance,
Stefan

---

### Post by smarf on 2008-07-24
Hi all,

perhaps I found the answer without solving the problem: it is a bug in exo-mount, found at [http://bugzilla.xfce.org/show_bug.cgi?id=2891](http://bugzilla.xfce.org/show_bug.cgi?id=2891)

Can someone affirm this? Will this be fixed in *ubuntu or will there be a patch?

Thank you - Stefan

---

### Post by Potatoj316 on 2008-07-24
I thought eject was the same thing as unmount

---

### Post by smarf on 2008-07-24
To my computer (why?) "unmount" means unmounting the partition (this is what I want but don't have a button for); instead "eject" means unmounting the marked partition and stopping the harddisk, removing the clicked icon and leaving zombie-icons of the other partitions of that harddisk on my desktop. So "unmount" is quite different to "eject", whereat the latter does not make sense to me for a partition.

---

### Post by Potatoj316 on 2008-07-24
Whenever I used eject in the past for multi partition drives it always took them all out.  Alternativly you could eject then mount manually.

---

### Post by smarf on 2008-07-24
Thank you for the hint. Indeed everything is unmounted, so this is not data critical (but leaves an invalid icon for each other partition of the already ejected drive).

The unwanted mount behavior still is an issue. I think the same problem was reported under [https://bugs.launchpad.net/ubuntu/+source/exo/+bug/193883](https://bugs.launchpad.net/ubuntu/+source/exo/+bug/193883) with patch, but I couldn't figure out if this patch would work for an up-to-date 8.04 XUbuntu nor how to install the patch.

So the main problem is: Files with non-latin-characters do not appear in Thunar and can not be created by rsync, if the partition is mounted using hal (ie.: the desktop icon). Calling "sudo mount X Y -o utf8" mounts correctly.

Which configuration file is to be changed and in what way?

Thank you in advance - Stefan

---

### Post by smarf on 2008-07-25
Hi there,

finally, after three complete re-installs, ntfs-config showed up to be the one. History:
- reinstall xubuntu through netinstall
- mount through command line (even without "-o utf8") works
- mount through graphical interface works
- install and run ntfs-config
- mount through command line needs "-o utf8"
- mount through graphical interface does not work

What files does ntfs-config change, and why does it affect utf8? :confused:

Thank you for helping me understanding this, best regards

---

