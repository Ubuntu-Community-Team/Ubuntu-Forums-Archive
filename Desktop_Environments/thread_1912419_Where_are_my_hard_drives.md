---
title: "Where are my hard drives?"
date: 2012-01-20
forum: Desktop Environments
---

### Post by natski on 2012-01-20
Hi all,

I have a server which had 11.04 server installed but was causing problems so I did a fresh install of ubuntu 10.04 desktop.

The machine has an SSD on which the OS were installed. The machine also has 3*2 TB disks for storage purposes. I cannot find the location of these drives after the fresh install.

I thought the drives should be located in /dev/sda1/ /dev/sda2/ and /dev/sda3/ or something similar. However, when I go into /dev/ there is a whole load of junk in there... here is the ls...

block            loop7               ram9        tty15  tty43    usbmon0
bsg              mapper              random      tty16  tty44    usbmon1
bus              mcelog              rfkill      tty17  tty45    usbmon2
cdrom            mem                 root        tty18  tty46    usbmon3
cdrw             mixer               rtc         tty19  tty47    usbmon4
char             net                 rtc0        tty2   tty48    usbmon5
console          network_latency     scd0        tty20  tty49    usbmon6
core             network_throughput  sda         tty21  tty5     usbmon7
cpu_dma_latency  null                sda1        tty22  tty50    vcs
disk             oldmem              sda2        tty23  tty51    vcs1
dvd              pktcdvd             sda5        tty24  tty52    vcs2
dvdrw            port                sequencer   tty25  tty53    vcs3
ecryptfs         ppp                 sequencer2  tty26  tty54    vcs4
fb0              psaux               sg0         tty27  tty55    vcs5
fd               ptmx                sg1         tty28  tty56    vcs6
full             pts                 shm         tty29  tty57    vcs7
fuse             ram0                snapshot    tty3   tty58    vcsa
hidraw0          ram1                snd         tty30  tty59    vcsa1
hidraw1          ram10               sndstat     tty31  tty6     vcsa2
hidraw2          ram11               sr0         tty32  tty60    vcsa3
hpet             ram12               stderr      tty33  tty61    vcsa4
input            ram13               stdin       tty34  tty62    vcsa5
kmsg             ram14               stdout      tty35  tty63    vcsa6
log              ram15               tty         tty36  tty7     vcsa7
loop0            ram2                tty0        tty37  tty8     vga_arbiter
loop1            ram3                tty1        tty38  tty9     zero
loop2            ram4                tty10       tty39  ttyS0
loop3            ram5                tty11       tty4   ttyS1
loop4            ram6                tty12       tty40  ttyS2
loop5            ram7                tty13       tty41  ttyS3
loop6            ram8                tty14       tty42  urandom

sda1 sda2 and sda5 are not folders so cannot be the location of these drives... where can I find them?

natski

---

### Post by LewisTM on 2012-01-20
Well.. sda1, sda2 and sda5 _are_ in your list. 
Of course they are not folders, /dev contains devices, not actual, immediately usable filesystems.

You might find them with
```
sudo blkid
```
and
```
sudo df
```
Find instructions online or in man pages on how to mount them e.g.
```
man mount
man fstab
```

Cheers!

---

### Post by stefangr1 on 2012-01-20
df only works for mounted partitions.

To detect the disks that are present, with their partitions, you can run:

```
sudo fdisk -l
```

After you found them, you may add them to your /etc/fstab such that they are mounted automatically.

---

