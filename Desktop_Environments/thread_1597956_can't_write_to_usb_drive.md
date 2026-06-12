---
title: "can't write to usb drive"
date: 2010-10-15
forum: Desktop Environments
---

### Post by dwpbike on 2010-10-15
i do 10.4.  as recently as two weeks ago, i could use my mp3 player as a usb drive.  now the player is still auto mounted, but i can't copy/paste to it or cut files from it.  i do see it in rhythmbox, but when i right click and choose "eject", the drive unmounts and the mount process starts over.  when i check permissions, i see that i am "read only".

---

### Post by inobe on 2010-10-15
when you remove the device and restart is it still mounted ?

also have you messed with any config files ?

---

### Post by dwpbike on 2010-10-17
thanks for the quick comeback.  just did a copy/paste on one machine and a cut/paste on other.  and it worked.  not aware i changed anything.  haven't used rhythmbox on this logon.

---

### Post by alexan on 2010-10-17
Take a look in the
/media
/mnt
folders


they should be empty while nothing (usbflash/cd) is plugged in.

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-17
Also check the settings on System > Administration > Disk Utility. But be careful not to change anything you don't know because you may end up with a formatted drive!

---

