---
title: "[SOLVED] Data recovery"
date: 2008-12-05
forum: General Help
---

### Post by callkalpa on 2008-12-05
I was using Ubuntu 8.10 and when I tried to install Fedora 10 to
another partition, I accidentally formated the Ubuntu partition. It's
file system was EXT3. How can I recover data in my formatted EXT3
partition ?

Any tool (even running under windows) ?

---

### Post by aysiu on 2008-12-05
You might be able to use *testdisk*, *gpart*, or *photorec*.

No guarantees, though.

You'll have to use a live CD and install those packages.

---

### Post by kuhlbeans on 2008-12-05
I remember using recover4all on Windows quite a while ago to recover some data but I'm not sure if it can read ext3 (perhaps it can read anything Windows can, in which case you can install the ext2 support for Windows and it should work).  Warning that it is a pay program for anything but very small files.

---

### Post by callkalpa on 2008-12-07
Thanks for all of you.
Got some files recovered using TestDisk.
Still couldn't see what and how they are :-)

---

