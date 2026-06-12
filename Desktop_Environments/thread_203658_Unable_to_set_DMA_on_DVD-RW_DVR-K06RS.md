---
title: "Unable to set DMA on DVD-RW DVR-K06RS"
date: 2006-06-25
forum: Desktop Environments
---

### Post by Entity on 2006-06-25
Hello,

I have an Acer Aspire 5672 WLMi with a Pioneer DVR-K06RS double layer drive. The problem is that when I try to enable DMA on this drive I get the following error message:

```
$ sudo hdparm -d1 /dev/cdrom

/dev/cdrom:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
```

Or if I try to get information about the drive I get the same error:

```
$ ll /dev/cdrom
0 lrwxrwxrwx 1 root root 4 2006-06-25 10:12 /dev/cdrom -> scd0
entity@laptop:~$ sudo hdparm -i /dev/scd0

/dev/scd0:
 HDIO_GET_IDENTITY failed: Inappropriate ioctl for device
```

Someone has an idea on what to do regarding that problem?

---

