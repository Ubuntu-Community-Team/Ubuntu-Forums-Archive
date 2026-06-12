---
title: "Boot without swap"
date: 2006-03-20
forum: Desktop Environments
---

### Post by pelagic on 2006-03-20
All~
I d'like to move a swap partition to the end of the disk so that I could make the ubuntu and w2k partitions bigger which are at the start of the disk. There was actually a 4th partition behind the swap that I don't need any more.
Obviously I can't move or delete the swap partition while ubuntu is running (tried it with gparted).
How could this be done properly?
Thanks for any hints!
pelagic


**Update**
and this is the partition table:

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

```
    Device Boot      Start         End      Blocks   Id  System
 /dev/hda1               1          13      104391   83  Linux
 /dev/hda2              14        1285    10217340   83  Linux
 /dev/hda3            3581        7296    29848770    f  W95 Ext'd (LBA)
 /dev/hda4   *        1286        3580    18434587+   c  W95 FAT32 (LBA)
 /dev/hda5            3581        3710     1044193+  82  Linux swap / Solaris
 /dev/hda6            3711        7296    28804513+   b  W95 FAT32

```

---

### Post by stuporglue on 2006-03-20
Using a live CD is an option. Post your partition table here, and we'll be able to help you better.

---

### Post by Ramses de Norre on 2006-03-20
You can just turn it off, I think it's swapoff disk_and_partition (e.g. swapoff sda5).

---

### Post by pelagic on 2006-03-20
[QUOTE=stuporglue]Using a live CD is an option. Post your partition table here, and we'll be able to help you better.[/QUOTE]
Of course, I posted the list in original question.
btw I'm talking about /dev/hda6

Thanks
pelagic

---

### Post by Ramses de Norre on 2006-03-20
```
sudo swapoff -a
```
Will turn all swap off, you can then edit the partitions and make a new swap partition, put it in /etc/fstab and then execute ```
sudo swapon -a
```

---

### Post by pelagic on 2006-03-21
Wel now w2k can't be booted any more! Heck I do **love** M$ ...

I did the folowing (see also first post of this thread):
[LIST]
[*]I turned off swap with swapoff
[*]I removed extended partition /dev/hda3 and the logical partitions therein /dev/hda5 and /dev/hda6
[*]I created a new swap partition (**primary** now) at the end of the disk /dev/hda3
[/LIST]

Partitions **before**:
```
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

    Device Boot      Start         End      Blocks   Id  System
 /dev/hda1               1          13      104391   83  Linux
 /dev/hda2              14        1285    10217340   83  Linux
 /dev/hda3            3581        7296    29848770    f  W95 Ext'd (LBA)
 /dev/hda4   *        1286        3580    18434587+   c  W95 FAT32 (LBA)
 /dev/hda5            3581        3710     1044193+  82  Linux swap / Solaris
 /dev/hda6            3711        7296    28804513+   b  W95 FAT32

```
Partitions **after**:
```
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1          13      104391   83  Linux
/dev/hda2              14        1285    10217340   83  Linux
/dev/hda3            7167        7296     1044225   83  Linux
/dev/hda4   *        1286        3580    18434587+   c  W95 FAT32 (LBA)

```

But then I can't get Windows booting properly. I get a message like:
```
Windows could not start because the following file is missing or
corrupt: <winnt root>\System32\Ntoskrnl.exe
```

I then mounted /dev/hda4 but found the file Ntoskrnl.exe in place.

Any ideas about **what **I screwed up here?
Thanks!
pelagic

---

### Post by pelagic on 2006-03-25
Just in case anyone is interested in the solution:

In the file **boot.ini** of W2K the numbering of the partitions had changed. As there is now a new **primary** partition /dev/hda3 that was a **logical** partition before, partition /dev/hda4 had now to be called:
multi(0)disk(0)rdisk(0)partition(4)\ ...
and not
multi(0)disk(0)rdisk(0)partition(3)\ ...
any more.
Thanks for all help!
pelagic

---

