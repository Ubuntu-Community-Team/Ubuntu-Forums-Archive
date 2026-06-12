---
title: "Error when hibernating"
date: 2009-04-24
forum: General Help
---

### Post by exodusofthemind on 2009-04-24
I am very new to ubuntu, but trying to pick things up quickly.
I've recently installed ubuntu 8.10 on my HP Mini 1030NR.

When I put my computer to sleep, I get an error message sometimes (not everytime) and I'm very curious what's happening.

This is the error code:
[93083.360919] sky2 000:02:00.0 eth1: phy I/O error
[93083.360976] sky2 000:02:00.0 eth1: phy I/O error
[93083.361058] sky2 000:02:00.0 eth1: phy I/O error
[93083.361112] sky2 000:02:00.0 eth1: phy I/O error
[93083.361161] sky2 000:02:00.0 eth1: phy I/O error

Note: It does display 5 times like that, then after about 2 minutes the system goes into hibernation.
The numbers inside the brackets seem to change every time I put the machine into hibernation.  


Any ideas? Or if someone could provide some clarification on what is happening that would be excellent.

---

### Post by jamessnell on 2009-04-24
I actually have never had the hibernation work properly on any of my Ubuntu installs. I believe it can work relatively easily, but I've never tried to actually troubleshoot it beyond a few mins of trial and error.

I personally use the Suspend feature all the time however and it works fairly well, at least on my macbook.

If you still want hibernation support, then I'd personally google it.. There's probably even a few great posts on the subject somewhere in this forum.

---

### Post by Monotoko on 2009-04-24
Is your swap on and bigger than your RAM?

EDIT: Seems its a problem with eth1, is your internet wired up when you go into hibernate...what happens if you disconnect it first?

---

### Post by exodusofthemind on 2009-04-24
Monotoko:
I'm not sure what swap is, or how to check the size. 

I use wireless only.

---

### Post by Monotoko on 2009-04-24
can you tell me how big your RAM is, then use ```
sudo fdisk -l
```

---

### Post by exodusofthemind on 2009-04-24
System has 1GB RAM

```
sudo fdisk -l

Disk /dev/sda: 16.3 GB, 16391208960 bytes
255 heads, 63 sectors/track, 1992 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1bfc1bfc

Device Boot Start End Blocks Id System
/dev/sda1 * 1 1903 15285816 83 Linux
/dev/sda2 1904 1992 714892+ 5 Extended
/dev/sda5 1904 1992 714861 82 Linux swap / Solaris

Disk /dev/sdb: 2019 MB, 2019556352 bytes
19 heads, 16 sectors/track, 12975 cylinders
Units = cylinders of 304 * 512 = 155648 bytes
Disk identifier: 0x00000000

Device Boot Start End Blocks Id System
/dev/sdb1 27 12976 1968127 b W95 FAT32
```

---

