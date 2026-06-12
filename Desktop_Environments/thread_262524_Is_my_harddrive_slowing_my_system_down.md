---
title: "Is my harddrive slowing my system down?"
date: 2006-09-21
forum: Desktop Environments
---

### Post by QwUo173Hy on 2006-09-21
I'm experiencing a lot of "stutters" in my Dapper installation (Breezy was fine). By stutters I mean split second loss of responsiveness every few minutes. I'm wondering if anyone could look at these results from hdparm and my fstab and tell me if they think my harddrive needs tuning.

```
ja@ja-laptop:~$ sudo hdparm /dev/hda

/dev/hda:
 multcount    = 16 (on)
 IO_support   =  1 (32-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 16383/255/63, sectors = 117210240, start = 0
ja@ja-laptop:~$ sudo hdparm -tT /dev/hda

/dev/hda:
 Timing cached reads:   560 MB in  2.00 seconds = 279.98 MB/sec
 Timing buffered disk reads:   62 MB in  3.08 seconds =  20.13 MB/sec
ja@ja-laptop:~$  
```                                          

And heres my fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,noatime,errors=remount-ro 0       1
/dev/hda3       /music          ext3    defaults,noatime,data=writeback        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Thanks for reading!

Jarlath

---

### Post by reclusivemonkey on 2006-09-22
> **jarlath said:**
> I'm experiencing a lot of "stutters" in my Dapper installation (Breezy was fine). By stutters I mean split second loss of responsiveness every few minutes. I'm wondering if anyone could look at these results from hdparm and my fstab and tell me if they think my harddrive needs tuning.


Not sure what you mean by "tuning"... does your hard drive make any strange noises? Are you sure the problem is with your hard drive? What are the other specs of your machine? Have you tried running "top" to see if that will help identifying the problem?

---

### Post by QwUo173Hy on 2006-09-22
No, there aren't any strange noises. I'm just trying to guess the most likely cause of the poor performance of my machine. It's an 800Mhz P3 with 320MB Ram. It's a laptop and the harddrive is 7200rpm.

I've run top in the background with an update every second to try to see whats causing it, but there's nothing that seems obvious to me. Amarok is always around 11%, konqueror jumps up to 33% occassionally, as does Xorg . These two seem to happen around the time of the 'stutters' I'm experiencing, but occasionally, I get a stutter and the CPU seems normal.

I've looked into konquerors performance options and loaded an instance into memory on startup. In future things may be a little better.

Does this sound normal?

---

### Post by reclusivemonkey on 2006-09-23
> **jarlath said:**
> No, there aren't any strange noises. I'm just trying to guess the most likely cause of the poor performance of my machine. It's an 800Mhz P3 with 320MB Ram. It's a laptop and the harddrive is 7200rpm.

I've run top in the background with an update every second to try to see whats causing it, but there's nothing that seems obvious to me. Amarok is always around 11%, konqueror jumps up to 33% occassionally, as does Xorg . These two seem to happen around the time of the 'stutters' I'm experiencing, but occasionally, I get a stutter and the CPU seems normal.

I've looked into konquerors performance options and loaded an instance into memory on startup. In future things may be a little better.

Does this sound normal?

Well, I don't have a laptop and I've never run KDE, so I can't really say what's "normal" for that. However, it just sounds to me that you CPU is maxing out at certain times. Also, 320Mb RAM is not quite "overburdened" with RAM; I am pretty sure that I read somewhere that you start to use Swap before your RAM is totally maxed. You could try running a more lighweight window manager and see if that helps.

---

### Post by QwUo173Hy on 2006-09-23
Thanks ReclusiveMonkey. I've been looking for a reason to upgrade my system for ages. If a lighter WM does the trick then I'll know.

All the best,
jarlath

---

