---
title: "dpkg unpacking takes very long time on Ubuntu 20.04 &amp; 20.10"
date: 2020-12-07
forum: Desktop Environments
---

### Post by funicorn on 2020-12-07
Some hardware information are attached below.

**uname**
 > Linux 5.8.0-31-generic #33-Ubuntu SMP Mon Nov 23 18:44:54 UTC 2020 x86_64 x86_64 GNU/Linux
**cat /sys/block/sda/queue/scheduler**
 > [mq-deadline] none
**df**
 > Filesystem     1K-blocks     Used Available Use% Mounted on
tmpfs 814632     1804    812828   1% /run
/dev/sda4      205414308 58017176 136892940  30% /
tmpfs            4073152   157196   3915956   4% /dev/shm
tmpfs               5120        4      5116   1% /run/lock
tmpfs               4096        0      4096   0% /sys/fs/cgroup
/dev/nvme0n1p1    200704    39108    161596  20% /boot/efi
tmpfs             814628     7524    807104   1% /run/user/1000
**lscpu**
 > Architecture:                    x86_64  
CPU op-mode(s):                  32-bit, 64-bit  
Byte Order:                      Little Endian  
Address sizes:                   48 bits physical, 48 bits virtual  
CPU(s):                          4  
On-line CPU(s) list:             0-3  
Thread(s) per core:              2  
Core(s) per socket:              2  
Socket(s):                       1  
NUMA node(s):                    1  
Vendor ID:                       AuthenticAMD  
CPU family:                      21  
Model:                           101  
Model name:                      AMD PRO A12-8870 R7, 12 COMPUTE CORES 4C+8G  
Stepping:                        1  
Frequency boost:                 enabled  
CPU MHz:                         1742.286  
CPU max MHz:                     3700.0000  
CPU min MHz:                     1400.0000
BogoMIPS:                        7385.68
Virtualization:                  AMD-V
L1d cache:                       64 KiB
L1i cache:                       192 KiB
L2 cache:                        2 MiB
NUMA node0 CPU(s):        0-3  
**fdisk -l**
 > Disk /dev/loop0: 97.74 MiB, 102486016 bytes, 200168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 55.32 MiB, 58007552 bytes, 113296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 97.86 MiB, 102612992 bytes, 200416 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 255.57 MiB, 267980800 bytes, 523400 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 217.89 MiB, 228478976 bytes, 446248 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 140 KiB, 143360 bytes, 280 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

---

