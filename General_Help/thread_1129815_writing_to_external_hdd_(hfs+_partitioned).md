---
title: "writing to external hdd (hfs+ partitioned)"
date: 2009-04-19
forum: General Help
---

### Post by eneloop on 2009-04-19
I'm using ubuntu 8.10 and tried changing permissions/owners with chmod and chown without any luck.

Is it possible to write to an hfs+ partitioned drive in ubuntu 8.10?

---

### Post by eneloop on 2009-04-25
any ideas?

---

### Post by eneloop on 2009-04-26
I've read Dirk.R.Gently's post from:

[http://ubuntuforums.org/showthread.php?t=392287](http://ubuntuforums.org/showthread.php?t=392287)

"The Linux HFS+ kernel driver has support to read and write to HFS+ non-journaled drives/parititions"

The external hdd partition I'm trying to write to is HFS+ non-journaled.

How do I write to this partition?

---

### Post by eneloop on 2009-05-01
any ideas?

---

### Post by eneloop on 2009-05-06
:confused:

---

### Post by Gideony on 2009-05-07
I'm right there with you, buddy.  Disabled journaling but I still can't write to the external drive.

On the properties page for the drive it says:
"permissions cannot be determined"

Under volume it says:
file system: hfsplus

---

### Post by @work on 2009-05-07
I see on google that youre hfsplus filesystem is a mac one. (please correct me if i'm wrong)

Did you try to install the filesystem on youre ubuntu machine? or is it installed? (best way to install = apt-get install from terminal)

perhaps use umount /whatyoumounted to umount it and su mount the filesystem you want it to use.

good luck!

xor

---

