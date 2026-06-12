---
title: "ddrescue"
date: 2022-07-02
forum: Desktop Environments
---

### Post by Geoff_Lane on 2022-07-02
Folks, had a mishap recently where I inadvertently formatted my main system drive (Ubuntu, Windoz and MX Linux multi Boot).

Gave me a good excuse to buy an SSD and reinstall.   Whilst I don't think I have lost any really important data I'd like to try and recover using testdisk.  I want to make a copy of disk with missing data and work on copy.   Am pretty familiar with dd but due to size of the disk (1TB) think I had better use ddrescue as it can resume if interrupted.  

My initial practice using ddrescue suggests it is much slower than dd, changing --sector-size=1M didn't appear to have any noticable effect.

Any suggestions appreciated, the original disk was not damaged in any way, just an accidental reformat.

Geoff

---

### Post by sudodus on 2022-07-02
I suggest that you read the info pages,

```

info ddrescue

```

I found a lot of useful information there, and I think you will find it useful too.

If there is nothing wrong the the drive itself, only with the file system on it, I don't think you need any special methods to succeed. I don't think you can expect that it will be fast, this is not the main advantage with ddrescue.

It is a good idea to learn how to use the logfile, so I suggest that you use it now, it is used when you resume the process. The logfile should be written to a third drive, not the source and not the target (but maybe to the drive with the running operating system).

[hr][/hr]
I helped a friend make useful video clips from two extremely scratched DVD disks (I think they were played during a sand storm in Sahara). It took more than one week for ddrescue to do the job :-P I have also recovered almost all the 'damaged' data from a hard disk drive from sectors that were initially considered bad. So ddrescue is really powerful.

---

