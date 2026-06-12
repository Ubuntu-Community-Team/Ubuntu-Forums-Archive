---
title: "Why Ubuntu switch to a text mode booting? how can I fix this?"
date: 2009-02-26
forum: General Help
---

### Post by arepaking on 2009-02-26
Hello experts,
When I boot Ubuntu it starts by showing the orange bar and the ubuntu logo, afterwards it switches to a text mode where it shows each process that is being load.

Does anyone knows how can I fix this so I can see only the orange bar loading up Ubuntu?

Thanks in advance,
AK

---

### Post by darco on 2009-02-26
Looks like the "quite splash" has been removed from the boot up script..on next boot up, highlight the current kernel, then hit the "e" key to edit. Type quiet at the last line. Then reboot

darco

---

### Post by caljohnsmith on 2009-02-26
Did you recently make any changes to your swap partition? I know that sounds strange, but if the UUID of your swap partition changes for any reason, you will usually lose your Ubuntu splash screen. How about posting the output of:
```
sudo fdisk -lu
sudo blkid -c /dev/null
cat /etc/fstab
cat /etc/initramfs-tools/conf.d/resume
```

---

### Post by arepaking on 2009-02-26
Thanks guys for your reply. I re-sized my home partition so maybe it is related to that.


Here is the information requested:
[B]
This is how my menu.lst looks like:[/B]
```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=16d08531-1119-444e-b426-e715ac675d4d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=16d08531-1119-444e-b426-e715ac675d4d ro  single
initrd		/boot/initrd.img-2.6.27-11-generic
```

[B]
sudo fdisk -lu (OUTPUT):[/B]
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x96089608

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   102398309    51199123+   7  HPFS/NTFS
/dev/sda2       102398310   625137344   261369517+   f  W95 Ext'd (LBA)
/dev/sda5       102398373   307194929   102398278+   7  HPFS/NTFS
/dev/sda6       307194993   408773924    50789466    b  W95 FAT32
/dev/sda7       408773988   419119784     5172898+  82  Linux swap / Solaris
/dev/sda8       419119848   448309889    14595021   83  Linux
/dev/sda9       448309953   625137344    88413696   83  Linux
```


[B]sudo blkid -c /dev/null
[/B]
```

/dev/sda1: UUID="2010CB7C10CB5784" TYPE="ntfs" 
/dev/sda5: UUID="CEF06341F0632F41" LABEL="Documents" TYPE="ntfs" 
/dev/sda6: LABEL="SOFTWAREMUS" UUID="4985-A766" TYPE="vfat" 
/dev/sda7: UUID="38e42948-4bc4-4516-9396-885025fd3aa8" TYPE="swap" 
/dev/sda8: UUID="16d08531-1119-444e-b426-e715ac675d4d" TYPE="ext3" 
/dev/sda9: UUID="c19d9c50-4d4e-47d7-966e-c3010447968c" TYPE="ext3" 
```


[B]
cat /etc/fstab[/B]
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=16d08531-1119-444e-b426-e715ac675d4d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=c19d9c50-4d4e-47d7-966e-c3010447968c /home           ext3    relatime        0       2
# /dev/sda7
UUID=561ec6e6-9bdb-4cc0-a3ae-86e07b8a4025 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
none  /proc/bus/usb  usbfs  auto,busgid=124,busmode=0775,devgid=124,devmode=0664  0  0
```


[B]
cat /etc/initramfs-tools/conf.d/resume[/B]
```
RESUME=UUID=561ec6e6-9bdb-4cc0-a3ae-86e07b8a4025
```


Thanks again!
-AK

---

### Post by lswest on 2009-02-26
Yeah, your UUID for swap changed.
Run the below from the terminal:
```
gksudo gedit /etc/fstab
``` then go to the line that reads > UUID=561ec6e6-9bdb-4cc0-a3ae-86e07b8a4025 none            swap    sw              0       0
 and change the UUID to > 38e42948-4bc4-4516-9396-885025fd3aa8

so the whole thing looks like the at the end:
```
UUID=38e42948-4bc4-4516-9396-885025fd3aa8 none            swap    sw              0       0
```

---

### Post by caljohnsmith on 2009-02-26
I would not recommend changing your fstab file to use the new swap UUID, because that will not help you get your Ubuntu splash screen back; the original swap UUID is hard-coded in all your /boot/initrd images files, so to get back your Ubuntu splash screen, you have to either regenerate all your initrd images so they use the new swap UUID, or much easier you can just change the UUID of your swap partition back to what it originally was:
```
sudo swapoff -a
sudo mkswap -U 561ec6e6-9bdb-4cc0-a3ae-86e07b8a4025 /dev/sda7
```
Reboot, and let me know if you get the splash screen OK, and also when you get back into Ubuntu please post:
```
free
sudo blkid -c /dev/null
```

---

### Post by arepaking on 2009-02-26
> **caljohnsmith said:**
> I would not recommend changing your fstab file to use the new swap UUID, because that will not help you get your Ubuntu splash screen back; the original swap UUID is hard-coded in all your /boot/initrd images files, so to get back your Ubuntu splash screen, you have to either regenerate all your initrd images so they use the new swap UUID, or much easier you can just change the UUID of your swap partition back to what it originally was:
```
sudo swapoff -a
sudo mkswap -U 561ec6e6-9bdb-4cc0-a3ae-86e07b8a4025 /dev/sda7
```
Reboot, and let me know if you get the splash screen OK, and also when you get back into Ubuntu please post:
```
free
sudo blkid -c /dev/null
```

You mean:

sudo mkswap -U 38e42948-4bc4-4516-9396-885025fd3aa8  /dev/sda7   right?

---

### Post by caljohnsmith on 2009-02-26
> **arepaking said:**
> You mean:

sudo mkswap -U 38e42948-4bc4-4516-9396-885025fd3aa8  /dev/sda7   right?
I think you might have misunderstood; using the above command won't change anything, because that is your current swap UUID. If you run the mkswap command from my post, that will change your swap UUID back to what it originally was, i.e. "561ec6e6-9bdb-4cc0-a3ae-86e07b8a4025". That way you won't have to change your fstab, resume file, and regenerate all your initrd images. :)

---

### Post by arepaking on 2009-02-26
> **caljohnsmith said:**
> I think you might have misunderstood; using the above command won't change anything, because that is your current swap UUID. If you run the mkswap command from my post, that will change your swap UUID back to what it originally was, i.e. "561ec6e6-9bdb-4cc0-a3ae-86e07b8a4025". That way you won't have to change your fstab, resume file, and regenerate all your initrd images. :)

IT WORKED!!!! thanks guys!!!

Here is the output for the commands above:

**free**
```
             total       used       free     shared    buffers     cached
Mem:       3103468     986028    2117440          0      20244     601900
-/+ buffers/cache:     363884    2739584
Swap:      5172888          0    5172888
```


**sudo blkid -c /dev/null**

```
/dev/sda1: UUID="2010CB7C10CB5784" TYPE="ntfs" 
/dev/sda5: UUID="CEF06341F0632F41" LABEL="Documents" TYPE="ntfs" 
/dev/sda6: LABEL="SOFTWAREMUS" UUID="4985-A766" TYPE="vfat" 
/dev/sda7: UUID="561ec6e6-9bdb-4cc0-a3ae-86e07b8a4025" TYPE="swap" 
/dev/sda8: UUID="16d08531-1119-444e-b426-e715ac675d4d" TYPE="ext3" 
/dev/sda9: UUID="c19d9c50-4d4e-47d7-966e-c3010447968c" TYPE="ext3" 
```


Thanks again!!

---

