---
title: "UDEV and e-SATA"
date: 2006-06-15
forum: Desktop Environments
---

### Post by hachaboob on 2006-06-15
I recently I purchased an e-SATA external hard-drive. I only guess that UDEV doesn't support hotplugging on SATA as a device in /dev isn't created unless the external is on while Linux boots up. Note: e-SATA is just a standard SATA connection that extends outside the square :)

I am not going back to slow USB2. Is there a UDEV mailinglist anywhere?

---

### Post by aurelieng on 2007-03-22
Same as [http://ubuntuforums.org/showthread.php?t=235647](http://ubuntuforums.org/showthread.php?t=235647) , but no reply yet :(

You found a trick ? Or are you still using USB2 ?

Cheers,

Aurélien.

---

### Post by knollbert on 2007-06-18
A solution that worked for me is to remove the module that controls your sata controller.  However, this only works if you have a seperate controller for your external drive.

---

