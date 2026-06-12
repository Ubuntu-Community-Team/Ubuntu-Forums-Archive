---
title: "How to recover lost EXT3 drive"
date: 2008-01-26
forum: Desktop Environments
---

### Post by rewolpert on 2008-01-26
:confused: I have a linksys network attached storage device.  The disks in it are formatted as EXT3.  The device crashed and now the disk is unreadable in the storage device.  Linksys is saying the disk is EXT3 format and if I hook it up to a Linux box I should be ablt to revover it.  I am very new to Linux however.  I have Ubuntu running but what do I do to recover the disk???: confused:

---

### Post by aysiu on 2008-01-27
You have two options: you can try *ddrescue* (it's confusing--the package name is *ddrescue*, but the command is *dd_rescue*), or you can install *testdisk* and use *photorec* (again, confusing--you're not using the *testdisk* command, but the *testdisk* package is the only way to install *photorec*).

---

