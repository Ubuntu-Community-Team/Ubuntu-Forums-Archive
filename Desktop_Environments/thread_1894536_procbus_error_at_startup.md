---
title: "procbus error at startup"
date: 2011-12-12
forum: Desktop Environments
---

### Post by misternails on 2011-12-12
On Ocelot 11.10. I recently installed VirtualBox 1.4, and there was a point were it complained about 'procbus' for the USB, so I tried to install that. The installation failed.
Now, VirtualBox is running great, and I don't really care about getting the USB to work in VirtualBox, but when I do a shutdown or system restart, I get an error message about 'procbus/Usb,' and it won't reboot unless I type 's' to skip.
How do I get rid of this annoying little procbus/usb message at startup?

---

### Post by misternails on 2011-12-15
Solved: procbus was a typo I made while modifying the last line of the fstab file, following the instructions located here: [https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)
under Karmic (because there was nothing for Ocelot).
This was all a result of the USB error in VirtualBox. After I fixed the fstab with "proc/bus" I was able to follow the rest of the instructions and successfully active the USB while in VirtualBox.

---

