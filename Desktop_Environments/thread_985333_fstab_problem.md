---
title: "fstab problem"
date: 2008-11-17
forum: Desktop Environments
---

### Post by deep_adhi on 2008-11-17
i wrote following code in my fstab 
/dev/sda5       /home/deepak/Documents/mine    vfat         defaults              0     0


but it does not allow me to write int this drive

---

### Post by hictio on 2008-11-17
What is this partition? What file system does it use? Are you suer it is not NTFS?
If it is a plain vanilla FAT file system, try mounting it like this:

```

/dev/sda5	/home/deepak/Documents/mine	vfat	auto,rw,uid=500 0 0

```

Change the 'uid' to reflect your own, get it by typing 'id' on a Terminal, the first entry, is your 'uid'.

---

