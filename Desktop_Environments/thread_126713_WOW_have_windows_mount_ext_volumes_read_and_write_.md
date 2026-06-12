---
title: "WOW have windows mount ext volumes read and write !!"
date: 2006-02-07
forum: Desktop Environments
---

### Post by cobelloy on 2006-02-07
There I was spewing about how my large newly formatted 220G partition (NTFS) was not writable with linux (created with windows of course) and how windowsXP refused to see it as a fat32, when I stumbled across this absolute gem - it is a self extracting/installing system file that allows windows explorer to have read and write access to ext2 (and ext3 mounted as ext2) volumes !!

Yes, you can actually save to your ext partitions from windows !!

of cousre - there is also a read only application [here]("http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm") but it does not have write access and not from within windows explorer

[ The Ext2 Installable File System for Windows]("http://www.fs-driver.org/index.html")

how cool is that!!??

---

### Post by Ocxic on 2006-02-07
very, but it can be unstable, and if windows just so happens to messup during a write it could crash the file system, it happend to me and i ended up reformatting. so i suggest being careful.

---

### Post by jezjones on 2006-02-07
Ok that may be useful, but it has been possible the other way (i.e. linux reading windows) for a long time! Since i spend 99% of my time in the linux partition that s the way i want it!

---

### Post by cobelloy on 2006-02-07
yeah, ubuntu reads/writes my 10gig windows system partition coz it is fat32, but this partition was over 32 gigs, linux could format it as fat32, but windows couldn't use it? and of course linux can't write to the partition as a ntfs - how do you get around that?

---

