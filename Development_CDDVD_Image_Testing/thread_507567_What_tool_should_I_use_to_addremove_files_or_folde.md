---
title: "What tool should I use to add/remove files or folders on a CD/DVD image?"
date: 2007-07-23
forum: Development CD/DVD Image Testing
---

### Post by PryGuy on 2007-07-23
Good day,
What tool should I use to add/remove files or folders on a CD/DVD image?
Thank you!

---

### Post by bernied on 2007-07-23
I don't know if there is a nice easy tool for this (sounds like a good idea though), but the old-fashioned way is something like [commands you need are in square brackets - you might need to adapt them]:

- create a mountpoint [sudo mkdir /mnt/tempiso]
- mount the .iso file [sudo mount -o loop /path/to/iso/file.iso /mnt/tempiso] (or just mount the cd/dvd) 
- copy the lot to a read/write filesystem (hard disk probably) [sudo cp -avx /mnt/tempiso/* /some/new/location]
- make the changes [whatever you want to do]
- create a new .iso [mkisofs] - but I'm hazy on the details of this command, 'man mkisofs' should tell you what to do.

---

### Post by PryGuy on 2007-07-23
Thanks a lot! Rule, Britain! ;)

---

