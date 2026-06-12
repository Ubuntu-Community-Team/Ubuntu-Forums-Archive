---
title: "Mounting /dev/md0 (RAID) on older kernel"
date: 2009-04-09
forum: General Help
---

### Post by wd5gnr on 2009-04-09
Trying to regress to an older kernel (that's another post).

When I boot it can't load my raid partition (where /home and /usr/local are). When I poke around in the shell it tells me the metadata is 0.90 and so is ignoring it. 

My normal kernel is 2.6.27-11 (either generic or a custom version; there seem to be problems with the sync of the source/image/headers in this version) and I'm trying to regress to 2.6.27-9-generic.

Do I have to "rebuild" the RAID (and I assume that won't shoot my data in the foot?).

---

### Post by askreet on 2009-04-09
It's very odd that 2 build numbers would have difference versions of linux md.  So odd, in fact, I don't believe it.

What is the output of dmesg relevant to md0?
$ sudo dmesg|grep md0

What is the output of /proc/mdstat?
$ sudo cat /proc/mdstat

What is the output of mdadm --detail?
$ sudo mdadm --detail /dev/md0

What is your favorite color?
$ sudo echo "Blue."

HTH,
askreet

---

### Post by wd5gnr on 2009-04-09
I'm not at that computer now (and behind a firewall) but this article seemed pertinent:

[http://ubuntuforums.org/archive/index.php/t-1007464.html](http://ubuntuforums.org/archive/index.php/t-1007464.html)

---

### Post by askreet on 2009-04-09
Interesting bug.  Sounds like you figured it out!

---

