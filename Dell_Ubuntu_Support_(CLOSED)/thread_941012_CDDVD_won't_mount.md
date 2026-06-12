---
title: "CD/DVD won't mount"
date: 2008-10-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by fishes on 2008-10-07
Hi,

I just installed Hardy on a Dell Optiplex GX270, and I'm unable to get CDs or DVDs to mount properly in my CD-RW/DVD-ROM drive. When I put a disc in, the status light blinks a few times, I can hear the drive moving around a bit, and then nothing. If I double click on the CD drive in the GUI I get "Unable to mount location, no media in the drive." I know the drive works, since I installed Hardy from it.

I then tried

```
sudo mount /media/cdrom0/
```

This got the CD to mount. I unmounted it, ejected, and put it back in. The drive would not mount the cd on it's own.

I put a DVD in and tried the same command line with a video DVD, and got

```
mount: No medium found
```

I don't know if this is important, but I do have restricted extras installed already.

I've installed Hardy on another GX270 and didn't have this issue, but I can't say for sure that the hardware was identical.

I'm new at this, so any help would be great. Thanks.

---

### Post by glyphobet on 2008-11-28
I was having a similar problem on Intrepid (8.10). 

Commenting out the line for my cdrom in /etc/fstab seemed to fix the problem, although I'm not sure why.

The line to comment out is the one containing "/media/cdrom". It will look something like this, although it may have any number of things right after "/dev/"

```
/dev/scd0  /media/cdrom0  udf,iso9660  user,noauto  0  0

```

If commenting out this line *doesn't* help then you should definitely put it back the way it was before, though.

---

### Post by don_m on 2009-01-07
I'm having a similar problem.

If I boot with CD or DVD in the drive, the media is found. I was doing some CD ripping and it seems I was able to maintain access to the CD or DVD player (a CD burner and DVD player is on my Compaq 5320).

If I boot with nothing in the drive and want to access something later, an error message of 'unable to mount' appears. I tried mount -a and some other commands, but the commands do not work.

Here is the fstab file:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=63908a60-d0f7-44db-bbb9-52ab630a5cf4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=f220c338-36f3-4854-8c8f-8f78e39c9d2f none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by fishes on 2009-02-04
After hitting my head on this for a while, I thought it might actually be hardware, since I didn't have a similar problem with 8.04 on a similar system. I finally scrounged up a replacement DVD drive and things seem to work.

---

### Post by wiresquire on 2009-02-05
I've had similar problems on a couple of machines of DVDs not playing/mounting.

The solution that worked for me was to *carefully* clean the laser lens using isopropyl alcohol on a cotton swab.

A lens cleaning kit/disk may work as well; i've never actually tried one.

hth
ws

---

### Post by fishes on 2009-02-05
You are probably right, and that would have been a bit easier than finding a new DVD drive.  This system has a laptop style DVD drive, so the head is exposed every time you open it. Probably very prone to finger print and dirt.

Thanks.

---

