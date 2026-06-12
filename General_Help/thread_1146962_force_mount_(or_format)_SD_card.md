---
title: "force mount (or format) SD card"
date: 2009-05-03
forum: General Help
---

### Post by alex_sv on 2009-05-03
Hi all,

I have an SD card which is not auto-discovered by my ubuntu laptop. I believe that it is still operable, i.e. it is broken at a filesystem level. Is it possible to recover SD card somehow - may be force mount filesystem or force format SD card?

My laptop is Dell Inspiron 1501, it has built-in SD reader. There is no problem with SD reader because it still operates on the other SD cards.

Would you please advise me a commands sequence/shell script/program that can turn my SD card back to life -or at least make a some sort of diagnostic work?

Thanks in advance,
Alexander 

P.S.:

lcpci shows the following ("broken" SD card is plugged in):
```

... <skipped> ...
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
...

```

contents of my /dev directory is as follows ("broken" SD card is plugged in):
```

audio            network_throughput  shm       tty38           usbdev3.1_ep00
block            null                snapshot  tty39           usbdev3.1_ep81
bus              oldmem              snd       tty4            usbdev4.1_ep00
cdrom            pktcdvd             sndstat   tty40           usbdev4.1_ep81
cdrw             port                sr0       tty41           usbdev5.1_ep00
char             ppp                 stderr    tty42           usbdev5.1_ep81
console          psaux               stdin     tty43           usbdev5.2_ep00
core             ptmx                stdout    tty44           usbdev5.2_ep81
cpu_dma_latency  pts                 tty       tty45           usbdev6.1_ep00
disk             ram0                tty0      tty46           usbdev6.1_ep81
dri              ram1                tty1      tty47           usbmon0
dsp              ram10               tty10     tty48           usbmon1
dvd              ram11               tty11     tty49           usbmon2
dvdrw            ram12               tty12     tty5            usbmon3
ecryptfs         ram13               tty13     tty50           usbmon4
fd               ram14               tty14     tty51           usbmon5
full             ram15               tty15     tty52           usbmon6
fuse             ram2                tty16     tty53           vcs
hidraw0          ram3                tty17     tty54           vcs1
hpet             ram4                tty18     tty55           vcs2
hwrng            ram5                tty19     tty56           vcs3
initctl          ram6                tty2      tty57           vcs4
input            ram7                tty20     tty58           vcs5
kmem             ram8                tty21     tty59           vcs6
kmsg             ram9                tty22     tty6            vcs7
log              random              tty23     tty60           vcs8
loop0            rtc                 tty24     tty61           vcsa
loop1            rtc0                tty25     tty62           vcsa1
loop2            scd0                tty26     tty63           vcsa2
loop3            sda                 tty27     tty7            vcsa3
loop4            sda1                tty28     tty8            vcsa4
loop5            sda2                tty29     tty9            vcsa5
loop6            sda3                tty3      ttyS0           vcsa6
loop7            sda4                tty30     ttyS1           vcsa7
MAKEDEV          sda5                tty31     ttyS2           vcsa8
mapper           sda6                tty32     ttyS3           xconsole
mem              sda7                tty33     urandom         zero
mixer            sequencer           tty34     usbdev1.1_ep00
mmcblk0          sequencer2          tty35     usbdev1.1_ep81
net              sg0                 tty36     usbdev2.1_ep00
network_latency  sg1                 tty37     usbdev2.1_ep81

```

---

### Post by delcypher on 2009-05-03
Sorry I don't know much about using SD card. [This guide I found may help you though.]("http://www.thinkwiki.org/wiki/How_to_get_the_internal_SD-CARD_working#Texas_Instruments_5-in-1_Multimedia_Card_Reader_.28SD.2FMMC.2FMS.2FMS_PRO.2FxD.29")

I found the [technical specs]("http://support.dell.com/support/edocs/systems/ins1501/en/om_en/html/specs.htm#wp1054574") for your laptop too, you may need to find the firmware for it.

---

### Post by alex_sv on 2009-05-03
Thank you for your answer...

I found that my SD flash drive is mapped to /dev/mmcblk0
Manual mounting does not work, manual format is not help either:

```

sasha@udellalex:/media$ sudo mount -t vfat /dev/mmcblk0 /tmp/mmc0
mount: /dev/mmcblk0: can't read superblock
sasha@udellalex:/media$ 
sasha@udellalex:/media$ sudo mkfs.vfat /dev/mmcblk0 
mkfs.vfat 3.0.1 (23 Nov 2008)
mkfs.vfat: failed whilst writing reserved sector

```

:(

---

### Post by alex_sv on 2009-05-03
... and yes, I checked lock switch. When it moved to the "LOCKED" state an output is as follows:

```

sasha@udellalex:/media$ sudo mount -t vfat /dev/mmcblk0 /tmp/mmc0
mount: block device /dev/mmcblk0 is write-protected, mounting read-only
mount: /dev/mmcblk0: can't read superblock

```

---

### Post by delcypher on 2009-05-03
Try opening the device with fdisk and sort out the partion tables.
```
sudo fdisk /dev/mmcblk0
```. Press m for help. There is a guide [here]("http://tldp.org/HOWTO/Partition/fdisk_partitioning.html")


Make sure the device isn't mounted when you do this.

---

### Post by alex_sv on 2009-05-03
thank you for your answer.

I tried fdisk but it does not help either:

```

sasha@udellalex:/media$ sudo fdisk /dev/mmcblk0 

Unable to read /dev/mmcblk0

```

Corresponding log output (dmesg) is as follows:

```

[25543.207280] mmcblk0: error -110 sending read/write command
[25543.207294] end_request: I/O error, dev mmcblk0, sector 0
[25543.207306] __ratelimit: 7 callbacks suppressed
[25543.207314] Buffer I/O error on device mmcblk0, logical block 0
[25543.207339] end_request: I/O error, dev mmcblk0, sector 8
[25543.207346] Buffer I/O error on device mmcblk0, logical block 1
[25543.207354] end_request: I/O error, dev mmcblk0, sector 16
[25543.207360] Buffer I/O error on device mmcblk0, logical block 2
[25543.207368] end_request: I/O error, dev mmcblk0, sector 24
[25543.207374] Buffer I/O error on device mmcblk0, logical block 3
[25543.212263] mmcblk0: error -110 sending read/write command
[25543.212270] end_request: I/O error, dev mmcblk0, sector 0
[25543.212277] Buffer I/O error on device mmcblk0, logical block 0
[25543.216852] mmcblk0: error -110 sending read/write command
[25543.216858] end_request: I/O error, dev mmcblk0, sector 1016
[25543.216865] Buffer I/O error on device mmcblk0, logical block 127
[25543.219020] mmcblk0: error -110 sending read/write command
[25543.219029] end_request: I/O error, dev mmcblk0, sector 1016
[25543.219036] Buffer I/O error on device mmcblk0, logical block 127
[25543.223241] mmcblk0: error -110 sending read/write command
[25543.223247] end_request: I/O error, dev mmcblk0, sector 0
[25543.223254] Buffer I/O error on device mmcblk0, logical block 0
[25543.223270] end_request: I/O error, dev mmcblk0, sector 8
[25543.223276] Buffer I/O error on device mmcblk0, logical block 1
[25543.223284] end_request: I/O error, dev mmcblk0, sector 16
[25543.223291] Buffer I/O error on device mmcblk0, logical block 2
[25543.223298] end_request: I/O error, dev mmcblk0, sector 24
[25543.225454] mmcblk0: error -110 sending read/write command
[25543.225471] end_request: I/O error, dev mmcblk0, sector 0
[25543.250152] mmcblk0: error -110 sending read/write command
[25543.250169] end_request: I/O error, dev mmcblk0, sector 0
[25543.250200] end_request: I/O error, dev mmcblk0, sector 8
[25543.250209] end_request: I/O error, dev mmcblk0, sector 16
[25543.250217] end_request: I/O error, dev mmcblk0, sector 24
[25543.258197] mmcblk0: error -110 sending read/write command
[25543.258212] end_request: I/O error, dev mmcblk0, sector 0

```


I believe that magic number "-110" is the complete description of I/O failures, but looks like digging into kernel is required in order to understand that...

---

### Post by delcypher on 2009-05-03
I'm pretty much out of ideas. I've never used SD cards and I don't have much experience. 

You could try a different partitioner tool like gparted.

My only other suggestion is try and fill the device with zeros and then try to fdisk the device again.


WARNING MAKE SURE /dev/mmcblk0 IS DEFINITELY YOUR SD CARD IF YOU GET THE DEVICE WRONG THINGS WILL GO VERY WRONG

to fill the device with zeros try this.```
dd if=/dev/zero of=/dev/mmcblk0 

```

I cannot guarantee this will work. Sorry.

---

### Post by alex_sv on 2009-05-03
Thank you for your help, I've quite an experience to work with the disk stuff :)

dd causes error as well as the others... Looks like, that my SD is damaged. (btw, looks like SD is nothing more but an ordinary flash card from linux driver's point of view - "All SD cards (other than microSD) can, at least, be accessed freely using the well-documented SPI/MMC mode." - taken from [here]("http://en.wikipedia.org/wiki/Secure_Digital_card")).

---

