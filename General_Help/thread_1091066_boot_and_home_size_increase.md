---
title: "/boot and /home size increase"
date: 2009-03-09
forum: General Help
---

### Post by prapanjganeshan on 2009-03-09
Hi,

I have installed Ubuntu Intrepid using wubi. I opted for 20 Gig space at installation on a partition that has 29 Gig free space. I am running some simulations on my machine and I am occasionally running out of disk space to hold the log files. I checked the free space on my /home folder ( by right clicking on the folder name and selecting 'properties'), it shows 0 bytes. But I haven't installed anything huge on the system so far. After deleting the log files I have free space of a few megabytes. When I view the properties of my /boot folder, I see 16 GB free space on it. 

My question is, is the /home folder on a separate logical partition? Why would /boot need so much space? How can I use more space for my /home folder? 

Your answers could be of great help to me. Thank you

---

### Post by prapanjganeshan on 2009-03-09
When I try to create a new text file using vim, it says "file system full?"  unable to write. This is how I know my problem is disk space.

---

### Post by prapanjganeshan on 2009-03-09
And this is the result on checking disk usage 

rwdi@ubuntu:~$ sudo df -k
[sudo] password for rwdi: 
Filesystem           1K-blocks      Used Available Use% Mounted on
/host/ubuntu/disks/root.disk
                       3844864    596912   3052640  17% /
tmpfs                  1681240         0   1681240   0% /lib/init/rw
varrun                 1681240       328   1680912   1% /var/run
varlock                1681240         0   1681240   0% /var/lock
udev                   1681240      2800   1678440   1% /dev
tmpfs                  1681240        12   1681228   1% /dev/shm
/dev/sda5             30701232  13528176  17173056  45% /host
lrm                    1681240      2000   1679240   1% /lib/modules/2.6.27-7-generic/volatile
/dev/loop1             3844864   3649700         0 100% /home
/dev/loop2             3844864   2908192    741360  80% /usr
/dev/scd0               715592    715592         0 100% /media/Ubuntu 8.10 i386
/dev/sda6             46082420   6784684  39297736  15% /media/windows


I checked the disk usage analyser. A few of the folders on which I run my simulations(programs) are full. Why don't the folders stretch their size when there is so much free space in other folders? Is there an option? Am I missing out on anything?

Thank you

Prapanj

---

