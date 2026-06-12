---
title: "Disk space reporting"
date: 2008-10-22
forum: Desktop Environments
---

### Post by dartrod on 2008-10-22
I used the partition editor to check my partition usage and was surprised to learn that my  /s/dev/sta1 partition usage was in my opinion extreme.

the partition size is 146.52 GB and usage is 104.3 GB  !!

I am using Ubuntu 8.04 and this was a fresh clean install about a month ago.

My PC configuration is:

AMD Athelon 64 LE 1640 2.6 GHZ 45 watt L2-1MB AM2
AMD Athelon 64 original Stock Fan and Heatsink
Kingston DDR2 PC2-5400 1GN/667 MHz
BIOSTAR MCP6P-M2 (NVIDIA GF6150, SATAII, RAID, DDR2-800
NVIDIA GeForce 6150 GPU Memory share upto 512MB
Onboard High Definition Audio
Onboard Network Card
450W ATX Power Supply
Western Digital CaviarSE 160GB 7200RPM SATA
LG DVD-RAM GSA-H55N
Ubuntu 8.04 Hardy Heron


Any explanation/help would be appreciated

RSW

---

### Post by dartrod on 2008-10-22
Further to my HD query.

I ran the following comnd an recieved these results.  

$ df -h -T
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext3     49G  6.0G   41G  13% /
varrun       tmpfs    442M  100K  442M   1% /var/run
varlock      tmpfs    442M     0  442M   0% /var/lock
udev         tmpfs    442M   72K  442M   1% /dev
devshm       tmpfs    442M   24K  442M   1% /dev/shm
lrm          tmpfs    442M   39M  403M   9% /lib/modules/2.6.24-21-generic/volatile
gvfs-fuse-daemon
fuse.gvfs-fuse-daemon     49G  6.0G   41G  13% /home/dartrod/.gvfs
/dev/sdf1     vfat    1.9G  322M  1.6G  17% /media/disk

The results are entirely different.

More help required.

RSW

---

### Post by angelopcs on 2008-10-24
I've got the same issue. I'm concerned, because I've run out of space once due to excessive log files.

---

### Post by Tanker Bob on 2008-10-24
Overgrown log files would be my guess. I ran into a similar problem a while back after a particularly long period of uptime. I had to change my work directory for DVD writing because I had run out of space on the root partition. After an unrelated restart (flash crash), everything was fine on restart. Have you tried simply restarting the system?

---

### Post by chrisvw on 2008-11-21
Moved my comment to a [new thread]("http://ubuntuforums.org/showthread.php?p=6228861#post6228861").

---

