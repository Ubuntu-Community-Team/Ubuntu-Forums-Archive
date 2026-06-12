---
title: "after using gparted"
date: 2006-10-01
forum: Desktop Environments
---

### Post by Magiczero on 2006-10-01
Hi

I used gparted to partion my 2nd hard drive and I get this error when I go to computer and the 2nd drive

> error: device /dev/hdb5 is not removable

error: could not execute pmount



I dont know what this is

Can someone help?
Please?
Thanks

---

### Post by tagra123 on 2006-10-01
try

sudo mkdir /media/hdb5partition
sudo chmod /media/hdb5partition
mount /dev/hdb5 /media/hdb5partition

What filesystem did you create on that partition?

Are you trying commands similar to above to mount it?

---

