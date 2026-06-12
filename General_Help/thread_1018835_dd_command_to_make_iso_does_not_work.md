---
title: "dd command to make iso does not work"
date: 2008-12-22
forum: General Help
---

### Post by fifth_rune on 2008-12-22
Hi all,

Trying to make an iso out of PSX game I have.  Made sure cd was unmounted first.  Used this command:

dd if=/dev/cdrom of=/home/david/Desktop/MYCD.iso

and I get this output:

> dd: reading `/dev/cdrom': Input/output error
40+0 records in
40+0 records out
20480 bytes (20 kB) copied, 2.6405 s, 7.8 kB/s


The actual file that gets spit out is only 20KB or so. I tried running the cd off an emulator to see if it works and it does, drive spins and everything so idk what's going on.  Any help?

---

### Post by Titan8990 on 2008-12-22
There is a good chance there is some kind of DRM protection on the PSX disc that is preventing you from copying it.

---

### Post by logos34 on 2008-12-22
what does 

isoinfo -i /dev/cdrom -d

show?

---

### Post by fifth_rune on 2008-12-22
Hm, it'd be interesting if there's DRM because I've ripped this to ISO before in Windows.

also, here's the output:

> CD-ROM is in ISO 9660 format
System id: PLAYSTATION
Volume id: CHRONOCROSS
Volume set id: SQUARE
Publisher id: SQUARE
Data preparer id: SQUARE
Application id: PLAYSTATION
Copyright File id: 
Abstract File id: 
Bibliographic File id: 
Volume set size is: 1
Volume set sequence number is: 1
Logical block size is: 2048
Volume size is: 313202
NO Joliet present
NO Rock Ridge present


---

### Post by mc4man on 2008-12-22
Here's some links, I take it to be something like this. (red is adjustable

```
cdrdao read-cd --read-raw --datafile [COLOR="Red"]image[/COLOR].bin --device /dev/scd[COLOR="Red"]0[/COLOR] --driver generic-mmc-raw [COLOR="Red"]image[/COLOR].toc
```

Or with wodim

```
readom dev=/dev/scd[COLOR="Red"]0[/COLOR] f=[COLOR="Red"]image[/COLOR].bin -clone retries=128 ts=128k
```

[http://www.megagames.com/psx/psx_copy_patch_linux.shtml](http://www.megagames.com/psx/psx_copy_patch_linux.shtml)

[http://psxemulator.proboards54.com/index.cgi?board=general&action=print&thread=2925](http://psxemulator.proboards54.com/index.cgi?board=general&action=print&thread=2925)

---

### Post by logos34 on 2008-12-22
[delete--probably wouldn't help]

---

### Post by Vantrax on 2008-12-22
Considering its copywrited material I would suggest you stop asking how to copy it here. Were not supposed to talk, or help, in regard to copying DRMed/copywrited materials. However im sure my trusty friend Mr Google has some advice on that.

Good Luck:P

PS I am serious, ive seen alot of threads like this locked, and users banned if they keep making them.

---

### Post by mc4man on 2008-12-23
while I'm certainly in no position to say if this thread is appropriate or not, I can say I don't see anything wrong here.

What fifth_rune is/was asking is technically no different than someone asking how to rip/dump an audio cd.

Nothing is present on that disc to prevent copying to a hdd, and that's all that was asked.

---

