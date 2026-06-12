---
title: "fstab entry for ReiserFS"
date: 2005-12-07
forum: General Help
---

### Post by audax321 on 2005-12-07
I just did a clean install of Breezy and am trying to mount a ReiserFS (v3.6) partition in read/write mode. The original entry in fstab was: 

/dev/hdb1       /media/Storage  reiserfs defaults        0       2

But, with this I can only write to the drive if I view it as root. This is just a drive to store random files on and I would like any user to be able to access it. Any help is appreciated. Thank you.

---

### Post by aysiu on 2005-12-07
*defaults* means no user (i.e., root only).
For more, read this:

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by poptones on 2005-12-07
You need to set permissions on the mounted folder to allow access.

chmod -R 777 /media/Storage

---

### Post by audax321 on 2005-12-07
Thanks, that did it.

Just mounted using: /dev/hdb1 /media/Storage reiserfs defaults 0 2
and
sudo chmod -R 777 /media/Storage
after mounting.

:)

---

