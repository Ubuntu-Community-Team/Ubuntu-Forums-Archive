---
title: "COD disk 1 wont unmount for disk 2"
date: 2009-11-30
forum: Gaming &amp; Leisure
---

### Post by crew51m on 2009-11-30
I try to load cod, when it asks for disk 2, it says app running and wont unmount. I tried a couple of times, same result. If all else fails, can I make a directory and copy the disks into the directory?

---

### Post by chewbakker82 on 2009-11-30
you could try copying the discs as .iso files and mounting them. Try this

make a directory for you to mount the iso to under /media. I made mine isomedia so i mount things to /media/isomedia. I then mount them with "mount" in terminal. 

sudo mount -o loop exampleisofile.iso /media/isomedia (or whatever directory you make)

To unmount,  umount /media/isomedia

That should work. That mount command is what I use for mounting DVD's and it should work for cd's and games.

---

### Post by crew51m on 2009-12-01
Thanks I will try.

---

