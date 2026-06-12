---
title: "Piecing together a RAID?"
date: 2009-05-20
forum: General Help
---

### Post by michealangelo on 2009-05-20
**Background info**
About 3 months ago I started my system off with 8.10. I have 5 hard drives in the system - 2 74GB, 1 160GB, 1 320GB, and 1 500GB. All 5 drives are used in a RAID (could possibly just be JBOD, I don't remember exactly). The first 74GB drive contains a 10GB partition for /, a 4GB partition for swap, and the rest is used toward the RAID.

**The problem**
Last night I decided I'd like to use the 64-bit version of 9.04. I formatted the ext3 & swap partitions and successfully installed 9.04. The problem is, I can't get the RAID to mount. What do I need to do to get this up and running again? Any help is greatly appreciated.

---

### Post by michealangelo on 2009-05-20
When following step 7 of this [guide]("http://ubuntuforums.org/showthread.php?t=408461"), terminal reads > mdadm: failed to create /dev/md0

I'm entering > mdadm --create /dev/md0 --chunk=64 level=5 --raid-devices=5 /dev/sda5 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1

Any ideas??

---

### Post by fjgaude on 2009-05-21
After booting up you might try this and then re-boot:

```
sudo mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf
```

This will create a new mdadm.conf file with a corrected UUID for the array.

Here's a good study link:

[http://www.hscripts.com/tutorials/linux-services/mdadm.html](http://www.hscripts.com/tutorials/linux-services/mdadm.html)

Have fun!

---

