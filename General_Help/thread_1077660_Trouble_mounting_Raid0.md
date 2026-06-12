---
title: "Trouble mounting Raid0"
date: 2009-02-22
forum: General Help
---

### Post by l0c0m0c0 on 2009-02-22
I know there's many guides for this but I can't seem to find anything that helps my exact situation.  

I have Vista installed on 2x 250gb Raid0 stripe.  I have Ubuntu installed on a separate Sata 250gb drive.  I successfully dual boot with no problems.  My dilemma is that I want to mount my NTFS Raid0 partition from Ubuntu.  

```

 sudo dmraid -ay
ERROR: isw device for volume "D00Mach1n3" broken on /dev/sda in RAID set "isw_bbecfadgga_D00Mach1n3"
ERROR: isw: wrong # of devices in RAID set "isw_bbecfadgga_D00Mach1n3" [4/2] on /dev/sda
ERROR: isw device for volume "2nd Volume" broken on /dev/sda in RAID set "isw_bbecfadgga_D00Mach1n3"
ERROR: isw: wrong # of devices in RAID set "isw_bbecfadgga_D00Mach1n3" [4/2] on /dev/sda
ERROR: isw device for volume "D00Mach1n3" broken on /dev/sdb in RAID set "isw_bbecfadgga_D00Mach1n3"
ERROR: isw: wrong # of devices in RAID set "isw_bbecfadgga_D00Mach1n3" [4/2] on /dev/sdb
ERROR: isw device for volume "2nd Volume" broken on /dev/sdb in RAID set "isw_bbecfadgga_D00Mach1n3"
ERROR: isw: wrong # of devices in RAID set "isw_bbecfadgga_D00Mach1n3" [4/2] on /dev/sdb

```

```

sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1043af6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       39163   314570752    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00330030

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe700e700

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       29286   235239763+  83  Linux
/dev/sdc2           29287       30515     9871942+   5  Extended
/dev/sdc5           29287       30515     9871911   82  Linux swap / Solaris

```

sda and sdb are my raid drives.  I have the raid setup through bios on my Asus Maximus Formula SE.  This is a fresh install all I have installed so far is dmraid.  Thanks.

---

### Post by fjgaude on 2009-02-22
After getting into Ubuntu install a program called **dmraid**. Read its **man** pages and then you will be able to mount NTFS drives.

Lots of things to learn herein.

```
sudo mdadm -ay
```

That will show the /dev/mapper name for your array.

Let us know how you are doing.

---

### Post by l0c0m0c0 on 2009-02-22
Thank you for the response.  I have installed dmraid previous to my first post.  I tried the command you listed above and I get :

command not found

---

### Post by fjgaude on 2009-02-22
Can you read the **man** pages?

```
man dmraid
```

If not, then **dmraid** is not installed.

---

