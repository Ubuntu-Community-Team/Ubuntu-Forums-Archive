---
title: "Error Reinstalling Grub"
date: 2009-06-14
forum: General Help
---

### Post by Tanner2007 on 2009-06-14
Hey guys I got big problem, I guess grub go jacked up so I looked at this guide

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

First i used the quick guide, and got this

```

   1.
      grub> setup (hd0)
   2.
       Checking if "/boot/grub/stage1" exists... yes
   3.
       Checking if "/boot/grub/stage2" exists... yes
   4.
       Checking if "/boot/grub/e2fs_stage1_5" exists... yes
   5.
       Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
   6.
      succeeded
   7.
       Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,5)/boot/grub/stage2
   8.
      /boot/grub/menu.lst"... failed
   9.
       
  10.
      Error 12: Invalid device requested
  11.
       
  12.
      grub>

```
So next i tryed the second one overwriting windows bootloader and got...
```



root@ubuntu:~# sudo grub-install --root-directory=/mnt/root /dev/sda
grub-probe: error: Cannot open `/boot/grub/device.map'
[: 494: =: unexpected operator
The file /mnt/root/boot/grub/stage1 not read correctly.


```


So what can i do? heres more info to

```

#
omitting empty partition (5)
#
 
#
Disk /dev/sda: 250.0 GB, 250059350016 bytes
#
255 heads, 63 sectors/track, 30401 cylinders
#
Units = cylinders of 16065 * 512 = 8225280 bytes
#
Disk identifier: 0x979a61e8
#
 
#
   Device Boot      Start         End      Blocks   Id  System
#
/dev/sda1   *           1       26003   208869066    7  HPFS/NTFS
#
/dev/sda4           26004       29255    26121690    5  Extended
#
/dev/sda5           26004       28681    21511003+  83  Linux
#
/dev/sda6           28682       29255     4610623+  82  Linux swap / Solaris

```

---

### Post by merlinus on 2009-06-14
You might try this:

```
 
sudo grub
root (hd0.4)
setup (hd0)
quit

```

---

### Post by camper365 on 2009-06-14
I have not done this, but you could try booting into a livecd, reformatting the partition you plan to use for /boot (I would recommend creating a separate 128 MB partition to use for /boot) and running sudo grub-install /dev/sda.
I don't know whether that has to have a grub already installed on the partition or not.

---

