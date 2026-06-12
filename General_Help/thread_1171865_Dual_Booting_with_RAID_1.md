---
title: "Dual Booting with RAID 1"
date: 2009-05-27
forum: General Help
---

### Post by jshufro on 2009-05-27
I have a pretty weird set up so I'll try to describe it as best I can.

Inside my computer there are three hard drives, a 500gb Seagate and two 680gb WDs.

The two 680 Western Digitals are set up in RAID 1 using a feature on my motherboard (probably software raid). I will refer to this as my media disk from now on. When I installed vista, I went into the registry and moved my C:\Users folder to D:\Users (on the raided media disk). This was a pretty long process, but ultimately I got it to work flawlessly. I even deleted my C:\Users folder. I always though this was analogous to using / on one hard drive and /home on a separate, raided array. It seemed smart.

Anyway, the first hard drive, the 500gb Seagate where I'm running vista, is split into two partitions. One 300gb one for vista and a 200gb one for Ubuntu.

So I decided to install Ubuntu today, having installed vista a month or so ago. Upon booting to the live CD and then rebooting, my raid array was marked as degraded.

I installed the OS anyway, and GRUB interestingly enough was showing 3 different boot options for Vista. Every time I booted to Ubuntu, though, the array was degraded again.

What do I do?

---

### Post by ronparent on 2009-05-28
Your setup for the raid is also known as so called fakeraid. The equivalent of a windows driver for the mb raid is a program in ubuntu called dmraid. Have you installed it? 

Once dmraid is installed and used to activate the raid, all read and writes are to the raid and not to the individual disks. I am thinking that perhaps you haven't activated the raid1. Could this account for the degraded array?

---

### Post by jshufro on 2009-05-28
I have not in fact installed dmraid. I will try this when I get home tonight.

---

### Post by jshufro on 2009-06-03
DMRAID is installed. I got some funky stuff going on.

Check this out.

```
jacob@JOSHUA:~$ sudo dmraid -s
*** Set
name   : nvidia_cgfeiace
size   : 1465149056
stride : 128
type   : mirror
status : ok
subsets: 0
devs   : 1
spares : 0
*** Set
name   : nvidia_bdbeidcj
size   : 1465149056
stride : 128
type   : mirror
status : ok
subsets: 0
devs   : 1
spares : 0

```

How do I get those two hard drives to play nicely into one mirror? Why are they in two different raid sets?

Edit:
More Info.
```

**jacob@JOSHUA:/dev/mapper$ ls -l**
total 0
crw-rw---- 1 root root 10, 61 2009-06-02 23:25 control
**jacob@JOSHUA:/dev/mapper$ sudo dmraid -ay**
ERROR: creating degraded mirror mapping for "nvidia_cgfeiace"
RAID set "nvidia_cgfeiace" was activated
ERROR: creating degraded mirror mapping for "nvidia_bdbeidcj"
RAID set "nvidia_bdbeidcj" was activated
RAID set "nvidia_cgfeiace1" was activated
RAID set "nvidia_bdbeidcj1" was activated
**jacob@JOSHUA:/dev/mapper$ ls -l**
total 0
crw-rw---- 1 root root  10, 61 2009-06-02 23:25 control
brw-rw---- 1 root disk 252,  1 2009-06-03 03:28 nvidia_bdbeidcj
brw-rw---- 1 root disk 252,  3 2009-06-03 03:28 nvidia_bdbeidcj1
brw-rw---- 1 root disk 252,  0 2009-06-03 03:28 nvidia_cgfeiace
brw-rw---- 1 root disk 252,  2 2009
**jacob@JOSHUA:/dev/mapper$ sudo dmraid -s**
*** Active Set
name   : nvidia_cgfeiace
size   : 1465149056
stride : 128
type   : mirror
status : ok
subsets: 0
devs   : 1
spares : 0
*** Active Set
name   : nvidia_bdbeidcj
size   : 1465149056
stride : 128
type   : mirror
status : ok
subsets: 0
devs   : 1
spares : 0

```

---

### Post by ronparent on 2009-06-03
This could be a tough one to unravel! My take is that the array was created twice, one for each drive? If right, you may have to delete one set  of metadata. This could be difficult to achieve without destroying your data. You may have to flee to the servers forum and plead for mercy.

Try **sudo dmraid -r** which might tell you which drive or drives each indicated array is associated with. If we can figger out how isolate and delete one set of raid data without trashing the integrity of the other we might be able to work it out. You can definitely save your data by removing one drive with the data intact. How to reassemble the drives as one array excedes my knowledge of dmraid syntax, though it should be possible.

---

