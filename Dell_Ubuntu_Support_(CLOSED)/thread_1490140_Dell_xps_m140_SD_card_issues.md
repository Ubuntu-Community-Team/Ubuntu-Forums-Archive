---
title: "Dell xps m140 SD card issues"
date: 2010-05-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vdubhack on 2010-05-21
Everytime my SD card mounts files with read only. The SD card has a bootable OS on it and when I try and view files from the disk on my 9.10 ubuntu the files are always read only. I have tried formatting it a few times with fdisk and gparted. When I checked dmesg it gave me a message I hadnt seen before 

[87726.840897] mmcblk0: error -123 sending status comand
[87726.840902] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[87726.853837] mmcblk0: error -123 requesting status
[87726.855837] end_request: I/O error, dev mmcblk0, sector 64
[87726.855843] Buffer I/O error on device mmcblk0p1, logical block 1
[87726.855846] lost page write due to I/O error on mmcblk0p1
[87726.862006] mmcblk0: error -123 sending status comand
[87726.862010] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[87726.874855] mmcblk0: error -123 requesting status
[87726.878003] end_request: I/O error, dev mmcblk0, sector 7424477
[87726.878008] Buffer I/O error on device mmcblk0p2, logical block 918019
[87726.878011] lost page write due to I/O error on mmcblk0p2
[87726.886006] mmcblk0: error -123 sending status comand
[87726.886011] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[87726.900016] mmcblk0: error -123 requesting status
[87726.906023] end_request: I/O error, dev mmcblk0, sector 64
[87726.906033] Buffer I/O error on device mmcblk0p1, logical block 1
[87726.906036] lost page write due to I/O error on mmcblk0p1
[87726.920135] mmcblk0: error -123 sending status comand
[87726.920140] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[87726.932129] mmcblk0: error -123 requesting status
[87726.934126] end_request: I/O error, dev mmcblk0, sector 0
[87726.934133] Buffer I/O error on device mmcblk0p2, logical block 0
[87726.934135] lost page write due to I/O error on mmcblk0p2
[87726.942005] mmcblk0: error -123 sending status comand
[87726.942009] mmcblk0: error -123 sending read/write command, response 0x0, card status 0x0
[87726.942013] end_request: I/O error, dev mmcblk0, sector 64
[87726.942025] FAT: bread failed in fat_clusters_flush
[87726.954432] MMC: killing requests for dead queue
[87726.954442] end_request: I/O error, dev mmcblk0, sector 64
[87726.954599] FAT: bread failed in fat_clusters_flush
[87726.954608] MMC: killing requests for dead queue
[87726.954612] end_request: I/O error, dev mmcblk0, sector 64
[87726.964786] FAT: bread failed in fat_clusters_flush
[87726.964809] MMC: killing requests for dead queue
[87726.964814] end_request: I/O error, dev mmcblk0, sector 1
[87726.964824] FAT: bread failed in fat_clusters_flush
[87730.610583] mmc0: new high speed SDHC card at address 7902
[87730.610720] mmcblk0: mmc0:7902 SD08G 7.42 GiB 
[87730.610780]  mmcblk0: p1 p2
[87731.497787] kjournald starting.  Commit interval 5 seconds
[87731.504274] EXT3 FS on mmcblk0p2, internal journal
[87731.504285] EXT3-fs: recovery complete.
[87731.752961] EXT3-fs: mounted filesystem with ordered data mode.


Does this mean the card is bad? Or is something else up with this?

---

