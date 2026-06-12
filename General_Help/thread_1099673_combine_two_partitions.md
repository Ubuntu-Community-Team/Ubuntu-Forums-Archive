---
title: "combine two partitions"
date: 2009-03-18
forum: General Help
---

### Post by sparky333 on 2009-03-18
I installed 8.04 Ubuntu on what I thought was my hard drive, but it actually got installed on my 1 TB USB external drive.
I didn't realize it until afterwards.  I partitioned the last 40GB for Ubuntu and now I want to release that. 
I've read here that I have to boot Ubuntu Live and use gparted.  Is this difficult?  Will it let me delete the right partition and increase the left by 40GB?

Thanks for any help...

---

### Post by Therion on 2009-03-18
I would suggest you boot to a gParted LiveCD (now called Parted Magic, actually):

[http://wiki.partedmagic.com/index.php/Downloads](http://wiki.partedmagic.com/index.php/Downloads)

You'll need to delete the existing 40GB partition and then expand the existing partition.  Very simple, very easy with Parted Magic.

---

