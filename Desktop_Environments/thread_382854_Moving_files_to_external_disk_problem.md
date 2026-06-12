---
title: "Moving files to external disk problem"
date: 2007-03-12
forum: Desktop Environments
---

### Post by eibon on 2007-03-12
Hi.

I'm trying to move/copy a directory with pictures in it to an external disk. The source is a ext3 disk, and the target is a vfat disk. The problem is, that when I move the files over to the external disk, there's a quite a few files left behind. Some of these, I can drag over manually. Others won't copy at all.

As far as I know, I have all the permissions needed for this operation. Still, I have tried opening nautilus with root access. Same thing happends. I should mention that the external disk is new, and works fine in windows.

Any thoughts?

---

### Post by geirha on 2007-03-12
You must NOT remove the external disk before you have right clicked on it (on the desktop) and selected unmount. If you remove it without unmounting, there is likely to still be files (or even parts of files) waiting to be written to the external drive, which you then will lose...

Could this be the problem?

---

