---
title: "stuck between fiesty and pclinux"
date: 2007-06-14
forum: Dell  Ubuntu Support
---

### Post by swoll1980 on 2007-06-14
had pc linux ,was trying to install fiesty guided use entire hard drive . Will notlet siad there was an error with ext3 device is busy , rebooted pclinux and it does not work either. I dont know what to do. is there a way to erase hard drive from bias or fix this somehow. please help!!:(

---

### Post by masterjonny on 2007-06-14
> erase hard drive from bias

If you mean you want to format, or change partitions etc. without booting an OS theres a variety of live CD's you can use. I reccomend [GParted]("gparted.sourceforge.net") for simplicity, but you could also use [Ultimate Boot CD]("www.ultimatebootcd.com"). 

Jus pop one of them in, find your Ext3 partition, delete it, then put back in the Feisty live CD and tell it to install again using the whole hard drive, should give better results.

Good luck getting it sorted.
x

---

