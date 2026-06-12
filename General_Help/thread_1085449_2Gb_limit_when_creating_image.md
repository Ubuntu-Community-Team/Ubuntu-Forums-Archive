---
title: "2Gb limit when creating image"
date: 2009-03-03
forum: General Help
---

### Post by max_spb_ru on 2009-03-03
I've got an Ubuntu 8.10 **32bit**. I'm trying to create dvd image(dvd size - 3.6Gb):
dd if=/dev/cdrom of=~/image.iso
but got only 2Gb file. Brasero behaves just the same. Is there the way to exceed this limit?

---

### Post by geirha on 2009-03-03
The kernel that ships with ubuntu has large file support, and dd and brasero are both compiled with large file support, so it doesn't make sense that it should stop at 2GiB. What filesystem is at the destination?

---

### Post by davidsrsb on 2009-03-03
I frequently build dvd iso images bigger than 2GB on Ubuntu 8.10 32 bit. My machines have a mixture of ext3 and jfs file systemes

As geirha suggests, what is your filesystem?

---

### Post by max_spb_ru on 2009-03-03
**geirha**
ext3

hmmm... ok. i'll try with another dvd. maybe this is a disk issue.

---

### Post by geirha on 2009-03-03
Hm. And it is not mounted through cifs or nfs or anything like that?

---

