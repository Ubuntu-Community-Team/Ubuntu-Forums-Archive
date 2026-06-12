---
title: "nvme ext4 root partition reports orphaned files on normal reboot cycle"
date: 2019-06-29
forum: Desktop Environments
---

### Post by tugurlann on 2019-06-29
Hello,

I have a dual boot set up where grub handles both unbutu 18.04 and a windows 10 installation.

Installation of ubuntu's *root partition* is on an smansung nvme drive, while */home* and */boot* have separate partitions on the same drive.

I have a strange problem whereas when I normally reboot the system wither via interface or with "reboot" from terminal, when the system comes back up i get orphaned files errors on the root partition.

The partition is "nvme1n1p17" and "journalctl | grep nvme1n1p7" returns the below
```


[    8.175265] EXT4-fs (nvme1n1p7): mounted filesystem with ordered data mode. Opts: (null)
[    8.412558] EXT4-fs (nvme1n1p7): re-mounted. Opts: errors=remount-ro
```

I suspect the somekind of a too fast reboot, or some files still being open when the system goes down. However, I lack the knowledge on how to approach such an investigation.

System specs: 8700k, z370 taichi, nvme drive + intel raid 0 ssds + 4tb hdd, nvidia card.

Any thoughts where should I look to monitor the shutdown process? Right now it is hidden behind the ubuntu graphical screen with the cycling dots, so maybe i should disable that first and get verbose shutdown?

Thank you.

---

### Post by TheFu on 2019-06-30
Hit the <esc> key to see dmesg output on boot or shutdown. It is written to tty7 by default.

You might want to enable persistent logging too.  In theory, you can use this and reboot:
```
sudo mkdir /var/log/journal
```
to enable that. Or change the journald.conf file line to this: 
```
Storage=persistent
```
from saying *auto*.  Then you can check the log files later using journalctl.

Reboot should cleanly shutdown all processes or wait a really long time before killing any that won't shutdown - like 90 seconds - at least - per process.

As for storage data, it is always better to SHOW the storage information than provide possibly incorrect descriptions.
```
lsblk
sudo fdisk -l  # that's an el, not a one.
df -hT -x squashfs -x tmpfs -x devtmpfs

```
are a start on providing useful information. Please.

---

### Post by tugurlann on 2019-08-09
Output from your suggestions below. I'm using an assortment of storage devices, including an HDD, a SATA SDD and 2 nvme SSD, a dynamic volume in windows which is used as caching drive for primo cache in windows as well.

Which log files should I inspect specifically?

```
NAME        MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
loop0         7:0    0 109,3M  1 loop  /snap/meteo/104
loop1         7:1    0   3,7M  1 loop  /snap/gnome-system-monitor/77
loop2         7:2    0   151M  1 loop  /snap/gnome-3-28-1804/40
loop3         7:3    0  31,3M  1 loop  /snap/adapta-gtk-snap/11
loop4         7:4    0  35,3M  1 loop  /snap/gtk-common-themes/1198
loop5         7:5    0 202,3M  1 loop  /snap/vlc/770
loop6         7:6    0  14,8M  1 loop  /snap/gnome-characters/258
loop7         7:7    0 108,1M  1 loop  /snap/meteo/101
loop8         7:8    0   7,5M  1 loop  /snap/canonical-livepatch/58
loop9         7:9    0  18,8M  1 loop  /snap/communitheme/1593
loop10        7:10   0   7,4M  1 loop  /snap/canonical-livepatch/74
loop11        7:11   0  14,8M  1 loop  /snap/gnome-characters/206
loop12        7:12   0  54,5M  1 loop  /snap/caprine/24
loop13        7:13   0     4M  1 loop  /snap/gnome-calculator/406
loop14        7:14   0     4M  1 loop  /snap/gnome-calculator/352
loop15        7:15   0  53,7M  1 loop  /snap/core18/970
loop16        7:16   0  34,8M  1 loop  /snap/gtk-common-themes/1122
loop17        7:17   0   8,4M  1 loop  /snap/canonical-livepatch/77
loop18        7:18   0 143,5M  1 loop  /snap/gnome-3-28-1804/23
loop19        7:19   0  1008K  1 loop  /snap/gnome-logs/61
loop20        7:20   0  88,4M  1 loop  /snap/core/6964
loop21        7:21   0  14,5M  1 loop  /snap/gnome-logs/45
loop22        7:22   0   3,7M  1 loop  /snap/gnome-system-monitor/81
loop23        7:23   0 143,5M  1 loop  /snap/gnome-calendar/28
loop24        7:24   0  80,7M  1 loop  /snap/gnome-calendar/52
loop25        7:25   0 104,2M  1 loop  /snap/whatsdesk/17
loop26        7:26   0 104,2M  1 loop  /snap/whatsdesk/14
loop27        7:27   0  91,1M  1 loop  /snap/core/6531
loop28        7:28   0  14,8M  1 loop  /snap/gnome-characters/254
loop29        7:29   0  53,7M  1 loop  /snap/core18/941
loop30        7:30   0  34,6M  1 loop  /snap/gtk-common-themes/818
loop31        7:31   0  28,6M  1 loop  /snap/adapta-gtk-snap/9
loop32        7:32   0 104,2M  1 loop  /snap/whatsdesk/15
loop33        7:33   0  1008K  1 loop  /snap/gnome-logs/57
loop34        7:34   0   151M  1 loop  /snap/gnome-3-28-1804/36
loop35        7:35   0 140,7M  1 loop  /snap/gnome-3-26-1604/82
loop36        7:36   0  28,6M  1 loop  /snap/adapta-gtk-snap/10
loop37        7:37   0   2,3M  1 loop  /snap/gnome-calculator/260
loop38        7:38   0  18,5M  1 loop  /snap/communitheme/1524
loop39        7:39   0 108,1M  1 loop  /snap/meteo/100
loop40        7:40   0 140,7M  1 loop  /snap/gnome-3-26-1604/74
loop41        7:41   0   3,7M  1 loop  /snap/gnome-system-monitor/70
loop42        7:42   0  53,7M  1 loop  /snap/core18/782
loop43        7:43   0 195,2M  1 loop  /snap/vlc/555
loop44        7:44   0 202,6M  1 loop  /snap/vlc/768
loop45        7:45   0    16M  1 loop  /snap/communitheme/1768
loop46        7:46   0 140,7M  1 loop  /snap/gnome-3-26-1604/78
loop47        7:47   0  89,3M  1 loop  /snap/core/6673
sda           8:0    0 232,9G  0 disk  
&#9492;&#9472;md126       9:126  0 465,8G  0 raid0 
  &#9500;&#9472;md126p1 259:14   0     1M  0 md    
  &#9500;&#9472;md126p2 259:15   0   127M  0 md    
  &#9492;&#9472;md126p3 259:16   0 465,7G  0 md    
sdb           8:16   0 232,9G  0 disk  
&#9492;&#9472;md126       9:126  0 465,8G  0 raid0 
  &#9500;&#9472;md126p1 259:14   0     1M  0 md    
  &#9500;&#9472;md126p2 259:15   0   127M  0 md    
  &#9492;&#9472;md126p3 259:16   0 465,7G  0 md    
sdc           8:32   0   3,7T  0 disk  
&#9500;&#9472;sdc1        8:33   0     3T  0 part  /media/SISKO
&#9492;&#9472;sdc2        8:34   0 656,1G  0 part  /media/STORAGE
nvme0n1     259:0    0 232,9G  0 disk  
&#9500;&#9472;nvme0n1p1 259:1    0     1M  0 part  
&#9500;&#9472;nvme0n1p2 259:2    0   127M  0 part  
&#9492;&#9472;nvme0n1p3 259:3    0 232,8G  0 part  
nvme1n1     259:4    0 232,9G  0 disk  
&#9500;&#9472;nvme1n1p1 259:5    0   499M  0 part  
&#9500;&#9472;nvme1n1p2 259:6    0   100M  0 part  /boot/efi
&#9500;&#9472;nvme1n1p3 259:7    0    16M  0 part  
&#9500;&#9472;nvme1n1p4 259:8    0  68,6G  0 part  
&#9500;&#9472;nvme1n1p5 259:9    0  98,9G  0 part  
&#9500;&#9472;nvme1n1p6 259:10   0   750M  0 part  /boot
&#9500;&#9472;nvme1n1p7 259:11   0    26G  0 part  /
&#9500;&#9472;nvme1n1p8 259:12   0  34,4G  0 part  /home
&#9492;&#9472;nvme1n1p9 259:13   0   3,6G  0 part  [SWAP]

```

```
fcmircea@hal9000-ubuntu:~$ sudo fdisk -l
[sudo] password for fcmircea: 
Disk /dev/loop0: 109,3 MiB, 114601984 bytes, 223832 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 3,7 MiB, 3821568 bytes, 7464 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 151 MiB, 158347264 bytes, 309272 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 31,3 MiB, 32821248 bytes, 64104 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 35,3 MiB, 37027840 bytes, 72320 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 202,3 MiB, 212099072 bytes, 414256 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 14,8 MiB, 15458304 bytes, 30192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 108,1 MiB, 113373184 bytes, 221432 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/nvme0n1: 232,9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 2D18CEEB-E848-4E4B-A018-8B9E7187CBEB

Device          Start       End   Sectors   Size Type
/dev/nvme0n1p1     34      2081      2048     1M Microsoft LDM metadata
/dev/nvme0n1p2   2082    262177    260096   127M Microsoft reserved
/dev/nvme0n1p3 262178 488397134 488134957 232,8G Microsoft LDM data


Disk /dev/nvme1n1: 232,9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 1B14417D-8E3C-4999-A670-34A8D502A2A5

Device             Start       End   Sectors  Size Type
/dev/nvme1n1p1      2048   1023999   1021952  499M Windows recovery environment
/dev/nvme1n1p2   1024000   1228799    204800  100M EFI System
/dev/nvme1n1p3   1228800   1261567     32768   16M Microsoft reserved
/dev/nvme1n1p4   1261568 145113087 143851520 68,6G Microsoft basic data
/dev/nvme1n1p5 145113088 352563199 207450112 98,9G Microsoft basic data
/dev/nvme1n1p6 352563200 354099199   1536000  750M Linux filesystem
/dev/nvme1n1p7 354099200 408690687  54591488   26G Linux filesystem
/dev/nvme1n1p8 408690688 480780287  72089600 34,4G Linux filesystem
/dev/nvme1n1p9 480780288 488396799   7616512  3,6G Linux swap


Disk /dev/sda: 232,9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x7e1478b8

Device     Boot Start        End    Sectors Size Id Type
/dev/sda1           1 4294967295 4294967295   2T ee GPT


Disk /dev/sdb: 232,9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sdc: 3,7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 9F510D3D-6EC7-11E8-9AB5-7085C25E45F2

Device          Start        End    Sectors   Size Type
/dev/sdc1        2048 6438154239 6438152192     3T Microsoft basic data
/dev/sdc2  6438156288 7814035455 1375879168 656,1G Linux filesystem


Disk /dev/md126: 465,8 GiB, 500113080320 bytes, 976783360 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 32768 bytes / 65536 bytes
Disklabel type: gpt
Disk identifier: F851E2E0-CE7B-03A9-B878-14FE9E73EA00

Device        Start       End   Sectors   Size Type
/dev/md126p1     34      2081      2048     1M Microsoft LDM metadata
/dev/md126p2   2082    262177    260096   127M Microsoft reserved
/dev/md126p3 262178 976783326 976521149 465,7G Microsoft LDM data

Partition 1 does not start on physical sector boundary.
Partition 2 does not start on physical sector boundary.
Partition 3 does not start on physical sector boundary.


Disk /dev/loop8: 7,5 MiB, 7839744 bytes, 15312 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 18,8 MiB, 19652608 bytes, 38384 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop10: 7,4 MiB, 7774208 bytes, 15184 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop11: 14,8 MiB, 15458304 bytes, 30192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop12: 54,5 MiB, 57126912 bytes, 111576 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop13: 4 MiB, 4218880 bytes, 8240 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop14: 4 MiB, 4214784 bytes, 8232 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop15: 53,7 MiB, 56328192 bytes, 110016 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop16: 34,8 MiB, 36503552 bytes, 71296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop17: 8,4 MiB, 8835072 bytes, 17256 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop18: 143,5 MiB, 150470656 bytes, 293888 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop19: 1008 KiB, 1032192 bytes, 2016 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop20: 88,4 MiB, 92733440 bytes, 181120 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop21: 14,5 MiB, 15208448 bytes, 29704 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop22: 3,7 MiB, 3821568 bytes, 7464 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop23: 143,5 MiB, 150474752 bytes, 293896 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop24: 80,7 MiB, 84639744 bytes, 165312 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop25: 104,2 MiB, 109252608 bytes, 213384 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop26: 104,2 MiB, 109211648 bytes, 213304 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop27: 91,1 MiB, 95522816 bytes, 186568 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop28: 14,8 MiB, 15462400 bytes, 30200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop29: 53,7 MiB, 56315904 bytes, 109992 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop30: 34,6 MiB, 36216832 bytes, 70736 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop31: 28,6 MiB, 30007296 bytes, 58608 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop32: 104,2 MiB, 109211648 bytes, 213304 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop33: 1008 KiB, 1032192 bytes, 2016 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop34: 151 MiB, 158343168 bytes, 309264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop35: 140,7 MiB, 147496960 bytes, 288080 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop36: 28,6 MiB, 30007296 bytes, 58608 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop37: 2,3 MiB, 2355200 bytes, 4600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop38: 18,5 MiB, 19435520 bytes, 37960 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop39: 108,1 MiB, 113369088 bytes, 221424 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop40: 140,7 MiB, 147496960 bytes, 288080 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop41: 3,7 MiB, 3846144 bytes, 7512 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop42: 53,7 MiB, 56315904 bytes, 109992 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop43: 195,2 MiB, 204644352 bytes, 399696 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop44: 202,6 MiB, 212406272 bytes, 414856 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop45: 16 MiB, 16769024 bytes, 32752 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop46: 140,7 MiB, 147496960 bytes, 288080 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop47: 89,3 MiB, 93581312 bytes, 182776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```

```
Sistem de fi&#537;iere  Tip     Dimens Utilizat Liber  Uz% Montat pe
/dev/nvme1n1p7     ext4       26G      17G  7,6G  69% /
/dev/sdc1          fuseblk   3,0T     1,4T  1,7T  47% /media/SISKO
/dev/nvme1n1p6     ext4      722M     162M  509M  25% /boot
/dev/nvme1n1p2     vfat       96M      30M   67M  31% /boot/efi
/dev/nvme1n1p8     ext4       34G      27G  5,6G  83% /home
/dev/sdc2          ext4      645G     266G  347G  44% /media/STORAGE
//192.168.1.50/BIG cifs      8,8T     8,2T  609G  94% /media/BIG

```

---

### Post by oldfred on 2019-08-09
I do not know RAID and TheFu is a better resource.

But this may be related as Linux does not like proprietary Microsoft dynamic partitions which are seen as LDM with gpt partitioning. 
> 
       /dev/nvme0n1p3 262178 488397134 488134957 232,8G [COLOR=#ff0000]Microsoft LDM data [/COLOR]



Microsoft often used dynamic partitions with MBR(msdos) as their work around for the 4 primary partition issue. Not sure why you would even want dynamic partitions on gpt partitioned drives, unless Microsoft is using it for something else.

       Shown as SFS, Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from)
[https://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv](https://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv)

---

