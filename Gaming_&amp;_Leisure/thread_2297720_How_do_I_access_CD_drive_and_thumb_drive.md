---
title: "How do I access CD drive and thumb drive?"
date: 2015-10-06
forum: Gaming &amp; Leisure
---

### Post by Kevin_Bjornson on 2015-10-06
I have the latest Ubuntu. 
I'm trying to install Civ 5 disks 
but when I go to Start menu
and click unto "Root", I can
see a file for CD-rom but it is empty. 

The Civ 5 disks are supposed to be for Microsoft OS,
but I heard that Civ 5 is native on Linux. Nothing about
Linux on the Civ 5 box. 

So I thought I would try to install and see what happens.
However nothing happens, I can't even access the CD drive. 

I had Ubuntu installed from a thumb drive,
but unfortunately I didn't catch how he got to it.

---

### Post by Bucky Ball on 2015-10-06
*Thread moved to **Gaming & Leisure**.*

If the disks are supposed to be for Windows and the box says nothing about Windows, then its for Windows. :)

Civ 5 may run natively on Linux, but not what you have, rather the native Linux version which has been created to run on Linux, not Windows.

(If you stick in a thumb drive or disk it will be picked up 'automagically' and you will be asked if you want to open a file manager. If that is not happening, the disks are probably just not recognised, which is in itself odd. Do you have this issue with other disks and USB drives?

If so, I'd post a thread specifically about this with as much detail as possible. I have moved this here as you are talking about two things in your original post, Civ 5 for Linux and USB thumb drives. Are the two related? We'll know that if you can insert other USB drives and disk without issue.

You will get help getting Linux native Civ 5 working here.

---

### Post by efflandt on 2015-10-06
Which Ubuntu version or variation are you running, because in regular Ubuntu (with Unity) I have not seen a "Start" menu or "Root".

But normally Ubuntu will automatically mount a CD/DVD inserted or USB storage (flash memory or drive) when plugged in and in some cases ask what you want to open it with if it detects certain media. If there are any problems you might open a terminal and type **dmesg** after inserting a CD or connecting USB to see if the tail end of that reveals any issues. Or if you want to scroll through dmesg you could type:```
dmesg | less
```

---

### Post by gordintoronto on 2015-10-08
Civilization 5 for Linux is available through Steam. It seems likely that you have the Windows version, which might work under Wine.

---

