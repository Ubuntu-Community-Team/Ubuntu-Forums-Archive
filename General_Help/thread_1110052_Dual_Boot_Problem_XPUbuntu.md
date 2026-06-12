---
title: "Dual Boot Problem XP/Ubuntu"
date: 2009-03-29
forum: General Help
---

### Post by RiSE69 on 2009-03-29
Hi,

I dual booted Ubuntu with Windows XP. I installed XP first and then Ubuntu on seperate partitions. Ubuntu works, but when I select windows XP in the grub list, it says "Invalid Device Requested". I only have one SATA Hard Drive, with a NTFS partition with windows on, a NTFS partition with data on, a ext partition with linux on, and a linux swap partition.

This is the output of (sudo fdisk -l):

> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44ae12a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2393    19221741    f  W95 Ext'd (LBA)
/dev/sda2   *        2394        4462    16619242+  83  Linux
/dev/sda3            4463       60801   452543017+   7  HPFS/NTFS
/dev/sda5               1        2284    18332968+   7  HPFS/NTFS
/dev/sda6            2285        2393      875511   82  Linux swap / Solaris


and this is the last part of the menu.lst file:

> title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		d764d380-b893-4f88-b10e-5407f174746f
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=d764d380-b893-4f88-b10e-5407f174746f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		d764d380-b893-4f88-b10e-5407f174746f
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=d764d380-b893-4f88-b10e-5407f174746f ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, memtest86+
uuid		d764d380-b893-4f88-b10e-5407f174746f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by SuperSonic4 on 2009-03-29
As windows is on sda3 you'll need to change (hd0,0) to (hd0,2) (ie: 3rd partition on 1st hdd)

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Microsoft Windows XP Professional
root (hd0,**2**)
savedefault
makeactive
chainloader +1 
```

---

### Post by RiSE69 on 2009-03-29
Thank you for the quick reply.

I changed it to hd0,2 and now it tells me hal.dll is missing. Any idea?

But why would it be on sda3, because I remember making my windows partition about 17gig. sda3 is like 450gig, that would be my data partition. Only one left is sda5:
/dev/sda5 1 2284 18332968+ 7 HPFS/NTFS

Just for interest sake, what is the partition in sda1:
/dev/sda1 1 2393 19221741 f W95 Ext'd (LBA)

---

### Post by SuperSonic4 on 2009-03-29
Ah right, I just guessed because as far as my knowledge goes XP can only be put on a primary partition but I could be wrong. Try (hd0,4) for sda5

---

### Post by RiSE69 on 2009-03-29
o wait, I think I know why it still works on the data partition. I found the boot.ini and ntldr files on it. Why would it get installed there? If i copy it over to the partition with windows on, will it work, and do i need to change any settings?

---

### Post by nebileix on 2009-03-29
> **RiSE69 said:**
> o wait, I think I know why it still works on the data partition. I found the boot.ini and ntldr files on it. Why would it get installed there? If i copy it over to the partition with windows on, will it work, and do i need to change any settings?

I guess you got to do a few tries on it. By looking at your section seems abit wierd... I might be wrong. Anyway, give it a try on (hd0,3).

---

