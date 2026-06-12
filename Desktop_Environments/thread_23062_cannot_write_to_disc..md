---
title: "cannot write to disc."
date: 2005-03-30
forum: Desktop Environments
---

### Post by berko on 2005-03-30
hello, i am having a problem burning cds using the "Write to disc..." menu command in gnome. it says my system is too slow to write at that speed. i have a 52x burner and i know it works because its worked before. i think it happened after a recent update.

it burns fine in k3b, just a lilltle slower than usual. it maxes out at about 22x. 

here is the detailed error output:
```
cdrecord: fifo was 0 times empty and 1 times full, min fill was 0%.
cdrecord: fifo had 64 puts and 0 gets.
cdrecord: Try to use 'driveropts=burnfree'.
cdrecord: Max DMA data speed is 17.
cdrecord: DMA speed too slow (OK for 17x). Cannot write at speed 48x.
cdrecord: WARNING: This causes a high risk for buffer underruns.
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
SCSI buffer size: 64512
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
Linux sg driver version: 3.5.27
Warning: Open by 'devname' is unintentional and not supported.
scsibus: -2 target: -2 lun: -2
devname: '/dev/hdd'
scsidev: '/dev/hdd'
cdrecord: WARNING: This causes a high risk for buffer underruns.
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: Warning: Running on Linux-2.6.10-5-k7
cdrecord: Continuing in 5 seconds...
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Asuming -tao mode.
cdrecord: No write mode specified.
```

---

### Post by berko on 2005-04-01
anybody?

---

### Post by LongTooth on 2005-04-01
berko, I don't know if you have Warty or Hoary on your machine. Open Synaptic and do a search for Gnomebaker. CD burning/copying has, for too long a time, been a sore spot for me in Gnome. Gnomebaker now comes to the rescue. I don't know if it's available for Warty. If it is not I would suggest you dist-upgrade to Hoary and install Gnomebaker. Do search on how to upgrade to Hoary. And ALL of your problems will be solved.


Better yet, after you upgrade to Hoary follow this HowTo   [http://ubuntuforums.org/showthread.php?t=22646](http://ubuntuforums.org/showthread.php?t=22646)  and surely you will have the best Linux experience of your life.

---

### Post by berko on 2005-04-02
i am using hoary. its been working fine like i said up until recently when i upgraded some packages through update manager.  for some reason i am suspecting problems with hdparm, or the kernel.  i will try gnomebaker tho. thanks for the reply.

---

### Post by berko on 2005-04-02
i just searched for gnomebaker in synaptic and its not there, what repository do i need to add?

---

### Post by Nano on 2005-04-02
[QUOTE=berko]i just searched for gnomebaker in synaptic and its not there, what repository do i need to add?[/QUOTE]
 For hoary:
[http://people.debian.org/~goedson/packages/ubuntu/hoary/gnomebaker/releases/](http://people.debian.org/~goedson/packages/ubuntu/hoary/gnomebaker/releases/)

---

### Post by berko on 2005-04-06
i am still having the same problem. i instsalled gnomebaker, and it works just the same as k3b, but i want to be able to burn from nautilus, and i want to be able to burn at 52x. any ideas anyone?

---

### Post by buildid on 2005-05-18
wARNING: This causes a high risk for buffer underruns.
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler

Found  something about this topic .

When run as root, cdrecord raises it's priority to make sure it gets
enough CPU to keep things flowing. Regular users can't do that, so you
get a warning message about it.

**Update** 
as sudo you wont see those messages , just checked that.

---

