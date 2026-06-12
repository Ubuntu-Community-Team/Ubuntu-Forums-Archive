---
title: "umount -f???"
date: 2006-07-18
forum: Desktop Environments
---

### Post by Freddy on 2006-07-18
Hi all.

Tried to install ut2k4 which comes on 5 cd's and after the first one was finished it asked me to mount cd2 and continue. When I tried to umount /media/cdrom0 it only stated that that device was buisy, so I tried to force the umount with -f but still it only said that the device was buisy.

I'm stuck, I checked with "man umount" but I cant see any "harder" way to force the umount, so please help me :-D.   /// Freddan

---

### Post by philippe_carlo on 2006-07-18
Did you happen to run the installer from the /media/cdrom0 directory?

---

### Post by Freddy on 2006-07-18
Yeah, I did. It's a installer.sh file and I run it from there.   /// Freddan

---

### Post by philippe_carlo on 2006-07-18
So, that's why your drive is locked. You need to run it from another directory, preferrably, your home directory.

---

