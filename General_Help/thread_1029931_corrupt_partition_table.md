---
title: "corrupt partition table?"
date: 2009-01-03
forum: General Help
---

### Post by drak10687 on 2009-01-03
Hi, new to ubuntu and linux, so I'll start from the begining.  I installed 8.10 a couple of weeks ago.  I had two NTFS partitions, one for XP and one for data... initially I just wanted to resize the XP one, but even after de-fragmenting and running chdisk several times the ubuntu liveCD partition editor didn't want to resize it, so I ended up formatting it into two NTFS partitions and installed ubuntu on one of them (I formatted to NTFS so I could use the first guided install option b/c I wasn't sure how to manually partition for linux).

Everything seemed to work fine... then today I wanted to install XP onto the remaining empty NTFS partition and be able to dual boot.  I read that I would have to reinstall grub afterwards, but it seemed like an easy enough procedure, so I went for it.

My problem starts now... when I boot from ubuntu 8.10 liveCD to reinstall grub, Gparted sees my entire drive as "unallocated", though fdisk and the browser (nautilus IIRC) detects them just fine.  Running sudo fdisk -lu gives me this:
```
ubuntu@ubuntu:~$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x08920892

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    40965749    20482843+   7  HPFS/NTFS
/dev/sda2        40965750    41110334       72292+   7  HPFS/NTFS
/dev/sda3        41110335   195350399    77120032+   f  W95 Ext'd (LBA)
/dev/sda4       102414438   195350399    46467981    7  HPFS/NTFS
/dev/sda5        41110461    99795779    29342659+  83  Linux
/dev/sda6        99795843   102414374     1309266   82  Linux swap / Solaris

```

it seems that it says that partition 5 is empty, though it goes on to list it (if sda5 = partition 5), and sda3 is inside of sda4... from searching around and reading about similar problems, it seems that there is something wrong here, but I'm not sure... and if there is, I'm not sure what to do about it.

Oh, I noticed the above after I tried:
```
grub> find /boot/grub/stage1
 (hd0,5)

grub> root (hd0,5)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 12: Invalid device requested

grub> 
```

I found a thread from a while back: [http://ubuntuforums.org/showthread.php?t=813199&highlight=repairing+partition+table](http://ubuntuforums.org/showthread.php?t=813199&highlight=repairing+partition+table)
which suggests to follow the instructions in this link: [http://tldp.org/HOWTO/Partition/fdisk_partitioning.html](http://tldp.org/HOWTO/Partition/fdisk_partitioning.html)
but I'm not sure if I have the same issue...

Is there anything I can do to fix the situation and be able to dual boot into my current XP and Ubuntu installs... or must I salvage as much data as I can from my data partition and start from scratch?

Thanks in advance for any help.

EDIT:
Wanted to add, that booting into XP, I just noticed that now I have a 3rd NTFS drive (E: ) which I didn't explicitly create that is 70.5Mb, 6.10 of which are free.

---

### Post by caljohnsmith on 2009-01-04
> **drak10687 said:**
> 
```
ubuntu@ubuntu:~$ sudo fdisk -lu
[COLOR="Red"]omitting empty partition (5)[/COLOR]

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x08920892

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    40965749    20482843+   7  HPFS/NTFS
/dev/sda2        40965750    41110334       72292+   7  HPFS/NTFS
[COLOR="Red"]/dev/sda3        41110335   195350399[/COLOR]    77120032+   f  W95 Ext'd (LBA)
[COLOR="Red"]/dev/sda4       102414438   195350399[/COLOR]    46467981    7  HPFS/NTFS
/dev/sda5        41110461    99795779    29342659+  83  Linux
/dev/sda6        99795843   102414374     1309266   82  Linux swap / Solaris

```

Unfortunately it looks like you do have a corrupt partition table. As you all ready noticed, fdisk notified you about "omitting empty partition(5)", which is always a sign of a corrupt partition table, but of more concern is the fact that your sda4 primary partition is inside of your sda3 extended partition; for sda4 to be inside of the extended partition, it should be a logical partition. How about posting the output of:
```
sudo sfdisk -d /dev/sda
```
And we can work from there if you want.

---

### Post by drak10687 on 2009-01-04
thanks caljohnsmith,

here's the output of sudo sfdisk -d /dev/sda :
```
ubuntu@ubuntu:~$ sudo sfdisk -d /dev/sda
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 40965687, Id= 7, bootable
/dev/sda2 : start= 40965750, size=   144585, Id= 7
/dev/sda3 : start= 41110335, size=154240065, Id= f
/dev/sda4 : start=102414438, size= 92935962, Id= 7
/dev/sda5 : start= 41110461, size= 58685319, Id=83
/dev/sda6 : start= 99795843, size=  2618532, Id=82

```

---

### Post by caljohnsmith on 2009-01-04
OK, just as a check, let's first make sure all your partitions can be mounted OK:
```
sudo mkdir /mnt/sda1 /mnt/sda2 /mnt/sda4 /mnt/sda5
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sda2 /mnt/sda2
sudo mount /dev/sda4 /mnt/sda4
sudo mount /dev/sda5 /mnt/sda5
ls -l /mnt/sda1 /mnt/sda2 /mnt/sda4 /mnt/sda5
```
Please post the output of all the above commands. If any of the mount commands return an error, please do not proceed with the rest of the directions in this post. But if all the partitions mount OK and show a directory listing with the last ls command above, then first make sure you have all your important data in all your partitions backed up, go ahead and download the attached "partition_table.txt" file to your desktop, and then do:
```
sudo sfdisk --force /dev/sda < ~/Desktop/partition_table.txt
```
That will produce a lot of output including some warnings, so don't be alarmed; but please post all the output. Then reboot, and next post the new output of:
```
sudo fdisk -l
sudo sfdisk -VluS
sudo sfdisk -d /dev/sda
```
And also post the output of:
```
sudo grub
grub> root (hd0,4)
grub> setup (hd0)
grub> quit

```
And we can work from there.

---

### Post by drak10687 on 2009-01-04
Well, backing up my data, I *just* had enough space on my external HDD to copy pretty much all of it... so I think I will just start from scratch: reinstall XP and then Ubuntu.  Not that I don't want to try to fix the partition table, but currently my partitions aren't exactly the way that I would like them to be, and since both installs are rather fresh, it shouldn't make too much difference time wise.

Thanks for your time and help anyways!

---

### Post by bodhi.zazen on 2009-01-04
If all else fails you can use testdisk to restore your partition table.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

