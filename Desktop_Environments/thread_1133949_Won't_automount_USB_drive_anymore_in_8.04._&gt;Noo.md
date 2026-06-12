---
title: "Won't automount USB drive anymore in 8.04. &gt;Noob&lt;"
date: 2009-04-23
forum: Desktop Environments
---

### Post by tpearson1 on 2009-04-23
First let me say that i have used this USB flash drive before on the same system. All of the sudden it won't automount anything, my ipod, other flash drives, anything.


i'm new to Ubuntu and i want to have a pleasant experience. I made the mistake of doing a clean install from vista to Ubuntu and now I want to dual boot Ubuntu and Windows XP.


running 8.04, thanks for any help.

---

### Post by tpearson1 on 2009-04-23
Don't forget about me!

---

### Post by maxim0512 on 2009-05-18
I am also having this problem in Hardy. Until recently, USB drives automounted without difficulty, but now they don't. If I restart the computer with the drive connected, it will mount, but if I connect a drive while the machine is running, the drive appears to receive power but the drive doesn't mount.

---

### Post by micio on 2009-05-18
please post the output of

```
dmesg | tail
```

Thanks,

Micio

---

### Post by ctmccaw on 2009-05-19
Hi all,

I've recently upgraded to Jaunty and I am having the same problem as mentioned above.

I've been searching the forums but haven't found any convincing solution just yet.

In previous incarnations of Ubuntu USB devices were automounting just fine whenever I plugged them in. Since the upgrade, they will automount if plugged in upon booting, but will not automount if plugged in during a session. I am able to mount the devices manually, and the devices are being recognised.

With the device plugged in, the output of dmesg | tail is

> dmesg|tail
[  245.993380] sd 7:0:0:0: [sdb] Write Protect is off
[  245.993383] sd 7:0:0:0: [sdb] Mode Sense: 45 00 00 08
[  245.993385] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  245.997369] sd 7:0:0:0: [sdb] 15695871 512-byte hardware sectors (8036 MB)
[  246.001375] sd 7:0:0:0: [sdb] Write Protect is off
[  246.001379] sd 7:0:0:0: [sdb] Mode Sense: 45 00 00 08
[  246.001381] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  246.001385]  sdb: sdb1
[  246.005846] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[  246.005877] sd 7:0:0:0: Attached scsi generic sg2 type 0

The output of blkid is:

> blkid
/dev/sda1: UUID="6018943C18941360" TYPE="ntfs" 
/dev/sda2: UUID="f7e38b39-575f-4842-9b67-f5c323971a46" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: TYPE="swap" UUID="49c8cc2d-cf43-4b68-9fda-6131717d5c84" 
/dev/sda4: UUID="A6E869F6E869C4E1" LABEL="shared_data" TYPE="ntfs" 
/dev/sdb1: LABEL="M-9^M-[}M-.&#65533;M-cM->^\M-Of" UUID="FC25-31F7" TYPE="vfat" 

sda1 is my windows partition, sda2 is Ubuntu, sda3 is swap, sda4 is a data partition that I share between XP and Ubuntu. I'm gathering sdb1 is the USB memory stick.

I'm dual-booting with Windows XP & I'm not a very sophisticated Linux user (yet!).

Any advice would be greatly appreciated.

Thanks!!

Pheppo.):P

---

