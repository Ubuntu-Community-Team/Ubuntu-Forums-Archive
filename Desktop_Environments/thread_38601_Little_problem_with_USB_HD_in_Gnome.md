---
title: "Little problem with USB HD in Gnome"
date: 2005-06-01
forum: Desktop Environments
---

### Post by nilus on 2005-06-01
I have an external usb hard drive.

The first time i used It, it was mounted automatically in /media/volume
After that, I edited my fstab then when i connect the usb hd to the pc it is mounted in  /mnt/hdusb. In console it works fine, but In Gnome I have a problem. When I try to access to the peripheral he advise me that he can't mount it because it has already  been mounted in another directory.
I think he have saved the first position (/media) while the new position is /mnt/hdusb.

The fstab line about the device is the seguent:
> /dev/sda1	/mnt/hdusb    	auto	noauto,user,exec,rw,umask=000	0	0 

How can I resolve the problem in Gnome using /mnt/hdusb directory?

Thanks :)

---

### Post by logan2004 on 2005-06-01
sudo umount /media/volume

---

