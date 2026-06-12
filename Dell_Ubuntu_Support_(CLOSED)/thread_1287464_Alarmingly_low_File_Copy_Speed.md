---
title: "Alarmingly low File Copy Speed"
date: 2009-10-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ecntrk on 2009-10-10
Hello Everyone,

I'm using Ubuntu Jaunty on my recently bought Dell Inspiron 1545 with 3GiB RAM and Core 2  Duo. During installation, I've made my / partition in **ext3** and also made 5 more partitions (four 50 and one 100 GiB) in **ext4**.


When I try to copy any file to and from anywhere, It's like seeing grass growing. The average speed is 600KBps. Sometimes it drops down to as low as 150 KBps.


Please suggest me something I can do with it.

Somewhere I read about testing speed by HdParam... I'm giving the output here...
Though this may seem more than ok, 60+MBps speed's showing here, I never achieved anything more than 1000KBps... :(

```
ecntrk@mithai:~$ sudo hdparm /dev/sdb

/dev/sdb:
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 1024/0/62, sectors = 0, start = 0
ecntrk@mithai:~$ sudo hdparm /dev/sdc
/dev/sdc: No such file or directory
ecntrk@mithai:~$ sudo hdparm /dev/sda

/dev/sda:
 IO_support    =  0 (default) 
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 38913/255/63, sectors = 625142448, start = 0
ecntrk@mithai:~$ sudo hdparm -d1 /dev/sda

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
ecntrk@mithai:~$ sudo hdparm -t /dev/sda

/dev/sda:

 Timing buffered disk reads:  180 MB in  3.01 seconds =  59.87 MB/sec
ecntrk@mithai:~$ 
ecntrk@mithai:~$ sudo hdparm -t /dev/sda

/dev/sda:
 Timing buffered disk reads:  190 MB in  3.02 seconds =  62.86 MB/sec
ecntrk@mithai:~$ sudo hdparm -T /dev/sda

/dev/sda:
 Timing cached reads:   2004 MB in  2.00 seconds = 1002.18 MB/sec
ecntrk@mithai:~$
```

---

### Post by fjgaude on 2009-10-10
Well, you are copying a file from one part of the drive to another... tough. In any event I would think your thru-put should be higher than 150 - 600 KB/sec.

You are talking about one big file at a time? Lots of smal files requires much CPU and disk activity, to seek, read, create, open, write. And you shouldn't be doing other things with the machine when copying, if max speed is needed for the copy process to proceed.

---

### Post by ecntrk on 2009-10-16
Thank you frank,

Yes, I know  that many files are bound to get slower than a large file while copying.
Unfortunately I get this rate even when I'm moving movies from one partition to another.


Any hope left for me? :(

---

