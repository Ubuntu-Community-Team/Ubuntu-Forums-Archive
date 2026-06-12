---
title: "can I create a ramdisk locally and make it appear on the desktop?"
date: 2008-03-10
forum: Education &amp; Science
---

### Post by wochi on 2008-03-10
Hi, all,
   The terminal memory size is getting bigger and bigger recently. I want to create a ramdisk using the terminal memory, but don't know howto configure so that the user can access it from the nautilus of the gnome. Anyone can help me? Thanks

---

### Post by bite on 2008-03-16
Don't know what the "terminal memory size" is but:
- I'm working with ubuntu 7.10 Gutsy Gibbon, standard kernel 2.6.22-14-generic (ramdisk support enabled by default)
- graunch 64Mb into /dev/ram1:
prompt> dd if=/dev/zero of=/dev/ram1 bs=1k count=65536
- make a file system there:
prompt> mke2fs /dev/ram1
- make a mount point (only necessary the first time):
prompt> mkdir /ramdisk
- mount /dev/ram1 onto the mount point:
prompt>  mount /dev/ram1 /ramdisk
and -voilà!- it magically appears on my desktop, with an icon which reminds me of an old style ISA board.
But if I copy something there then umount the ram disk, of course it gets lost.
So be careful, if you intend to store there something more than temporary files, you should save your precious work before umounting, and be prepared to lose it in case of power failure.

---

