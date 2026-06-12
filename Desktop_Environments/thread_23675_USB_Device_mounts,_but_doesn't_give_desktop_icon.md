---
title: "USB Device mounts, but doesn't give desktop icon?"
date: 2005-04-03
forum: Desktop Environments
---

### Post by ming0 on 2005-04-03
When I plug in a UMS (USB Mass Storage) device (camera, mp3 player), Ubuntu (hoary, latest updates) mounts it, but doesn't give me a desktop icon to unmount the drive with!

CD's still put icons on the desktop, and UMS devices *used* to give me an icon; however, I don't remember if it was the motherboard upgrade, or the switch to hoary (or some other factor) that caused this change.

To be sure, I *completely removed,* and subsequently reinstalled the following packages:

gnome-volume-manager
hwdb-client
hal
hal-device-manager

But I still have the same problem :-s

Anyone have experience with this?

---

### Post by jonny on 2005-04-04
An update to HAL seemed to introduce this problem a couple of weeks back.  If you search the forums, you'll find lots of hints and tips (mostly centred around running something like /etc/init.d hal restart), but none worked for me.

---

### Post by ming0 on 2005-04-04
That's odd, I don't even have an /etc/init.d/hal section? Maybe that's it....

---

### Post by ming0 on 2005-04-06
Like magic, the most recent update seems to have fixed this annoying bug! \\:D/

---

### Post by bestiarosa on 2006-08-12
I still have this problem with the latest upgrade of Ubuntu Dapper Drake. I have created a shortcut to my USB device but this sucks because I still have to manually umount it.
Is there anything I can do to make Ubuntu show the device icons on my desktop so I can umount from the icon?

---

