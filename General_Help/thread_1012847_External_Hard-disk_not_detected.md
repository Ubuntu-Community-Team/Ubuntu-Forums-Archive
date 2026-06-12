---
title: "External Hard-disk not detected"
date: 2008-12-16
forum: General Help
---

### Post by 7raTEYdCql on 2008-12-16
Today i bought a External Hard-disk(Maxtor-500gb).

Plugged it in and it is not detected. Unlike pen-drives which automatically get detectd

Am i supposed to format the disk? Mount the disk? 

This is the first time i have got an external hard-disk. And just to notify on the cover there was a mentioning that the hard-disk is compatable with
"Windows Vista, Windows XP, or Mac OS X 10.4.8 or higher"
Will this be the cause of it not automatically mounting.

Please i am a little worried.

---

### Post by taurus on 2008-12-16
See if the new external harddrive shows up from the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by 7raTEYdCql on 2008-12-16
This is my output with sudo fdisk -l
[output]mehrzad@mehrzad-laptop:~$ sudo fdisk -l
[sudo] password for mehrzad: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000093fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14651248+  83  Linux
/dev/sda2            1825        1886      498015   82  Linux swap / Solaris
/dev/sda3            1887       19457   141139057+  83  Linux
mehrzad@mehrzad-laptop:~$ 

[/output]

I dont think it is detected.

---

### Post by LinuxPS2 on 2008-12-16
well I know I have had some trouble with external NTFS drives in which case you can just use ntfs-config to do it - here is a simple guide [http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html")

hope that helps...

--L|nuxPS2

---

### Post by taurus on 2008-12-16
Is it plugged in and on?  Otherwise, you can plug it into windows machine and create a partition, probably something like /dev/sdb1, and format it to ntfs filesystem.  Then, boot into Ubuntu and see if it is mounted.

---

### Post by 7raTEYdCql on 2008-12-16
I am a total noob.How do i format it to NTFS?

Do i need to use a windows cd?

---

### Post by 7raTEYdCql on 2008-12-16
Can i format to ntfs in ubuntu itself?

---

### Post by LinuxPS2 on 2008-12-16
yes, you could see if it shows up with gparted... if it does but it does not show a partition you could always just use gparted to create the partition... i think you have to have ntfsprogs installed if you want gparted to format as NTFS though...

---

### Post by 7raTEYdCql on 2008-12-16
It is not showing up on gparted.

---

### Post by 7raTEYdCql on 2008-12-16
I dont even know whether the external is formatted in the first place or no.

---

### Post by taurus on 2008-12-16
What's the output of this command?

```
dmesg | tail
```

---

### Post by any.linux12 on 2008-12-16
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config

---

### Post by 7raTEYdCql on 2008-12-16
And i dont have a working windows machine(...hahaha...)to check it.

---

### Post by 7raTEYdCql on 2008-12-16
[   61.002174] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   61.399873] NET: Registered protocol family 17
[   67.447103] eth0: no IPv6 routers present
[  105.993867] tg3: eth0: Link is down.
[  106.254007] tg3: eth0: Link is up at 100 Mbps, full duplex.
[  106.254014] tg3: eth0: Flow control is off for TX and off for RX.
[  106.257485] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  109.010932] eth0: no IPv6 routers present
[ 1591.619533] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[ 1591.619561] VMBlock warning: DentryOpRevalidate: invalid args from kernel

---

### Post by 7raTEYdCql on 2008-12-16
I installed ntfs-config. Dont know doesnt seem to work.

I get the option "Enable write support for the external device."

After clicking on OK, there is not further response.

---

### Post by taurus on 2008-12-16
> **i.mehrzad said:**
> I installed ntfs-config. Dont know doesnt seem to work.

I get the option "Enable write support for the external device."

After clicking on OK, there is not further response.

it's because Ubuntu has not detected your new external harddrive so that command is useless for now.  Is the power of the drive on or is there even a power switch on the drive?

What is the exact model of that Maxtor?

---

### Post by any.linux12 on 2008-12-16
do you have usbsf?
and what about you fstab??

---

### Post by 7raTEYdCql on 2008-12-16
Yes the power on my external is on.

There is not model number as such, It just says, Maxtor Basics(500Gb)

---

### Post by 7raTEYdCql on 2008-12-16
Just asking whether i need to change anything in /etc/fstab

---

### Post by 7raTEYdCql on 2008-12-16
I dont have usbsf. My synaptic doesnt mention anything about this package?

---

### Post by scouser73 on 2008-12-16
I have four external Maxtor Basics 500GB HDDs, by rights it should be automatically detected, as it's not here's what I suggest you do.

1 - Go to Synaptic Package Manager
2 - Search for Gparted
3 - Mark for installation and apply the changes
4 - Go to System, Administration, Partition Editor & select
5 - Select your hard drive from the drop-down menu, (usually it's /dev/sdX) where X is your drive letter
6 - Click Device, & Create Partition Table, & click Apply
7 - Click New, and then the Filesystem drop-down menu and choose either ext2. ext3 or reiserfs and apply.

Personally, I always choose reiserfs.

---

### Post by LinuxPS2 on 2008-12-16
> **scouser73 said:**
> I have four external Maxtor Basics 500GB HDDs, by rights it should be automatically detected, as it's not here's what I suggest you do.

1 - Go to Synaptic Package Manager
2 - Search for Gparted
3 - Mark for installation and apply the changes
4 - Go to System, Administration, Partition Editor & select
5 - Select your hard drive from the drop-down menu, (usually it's /dev/sdX) where X is your drive letter
6 - Click Device, & Create Partition Table, & click Apply
7 - Click New, and then the Filesystem drop-down menu and choose either ext2. ext3 or reiserfs and apply.

Personally, I always choose reiserfs.

I thought he said it didn't show up in gparted?...

---

### Post by albino.hernandez on 2008-12-17
I have same problem, in my case is maxtor 250 gigas, it powers on when connected to usb port, it was used first to back up a pc with windows xp, then I plug it to this pc that works xubuntu   with no problem whatsoever (i coud see all files previously store from the win pc)                                                                             but after i did some ubuntu upgrades it is not detected anymore,  any ideas why?
my sound card was also no longer detected but after changing to another pci slot solved the problem, but with this external hd i am lost.                                                                                                                    to

---

