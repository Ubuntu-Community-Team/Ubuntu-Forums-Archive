---
title: "Ubuntu/XP Dual Boot, XP Login Problems"
date: 2009-01-24
forum: Desktop Environments
---

### Post by RikkiUW on 2009-01-24
Hello all. I decided I could not call myself a computer geek without some sort of Linux experience, so installed Ubuntu on my desktop and laptop. 

I didn't have any problems with my laptop, it resized the partition and installed perfectly, but it didn't recognize the existing partition on my Desktop. I ended up using Acronis PartitionExpert to resize the partition and install Ubuntu on the newly created free space. Ever since I have trouble logging into XP. It starts loading and explorer freezes when my AV program (NOD32) starts loading. I end up having to stop and restart explorer.exe, often multiple times, before it unfreezes, then I have problems because not all of the processes/startup programs have started. The wireless service not starting is the biggest problem/inconvenience. This happens every time I try to log in. I have performed a repair of XP and done a disk check in case PartitionExpert messed up my partition, and am still having problems. Ubuntu works perfectly fine, it's just XP that's screwed up. Does anyone have any suggestions before I reformat XP? Doing that would be really, really inconvenient.

Microsoft really aught to learn how to play nice. Thanks in advance for any help.

--Rikki

---

### Post by RikkiUW on 2009-01-26
Anyone?

---

### Post by caljohnsmith on 2009-01-26
So have you done:
```
chkdsk /r
```
on the Windows partition?

---

### Post by johnjohn2 on 2009-01-26
Also try running Defrag on XP as windows does like it's file system to remain untouched! Acronis may have disturbed something!


If these don't work then i am afraid it is reinstall time and if you have to make sure you set up the partitions prior to installing XP.

And for the love of god install XP first

Regards john

---

### Post by RikkiUW on 2009-01-26
I did a checkdisk by right clicking one c drive and choosing both options for check disk (fix file system errors, scan and attempt recovery of bad sectors) which I believe is the equivelent.

I ran Auslogic Disk Defrag. I kinda figured I'd have to reformat, guess I'll have to do it on Saturday.

I'm curious though, why do you think Ubuntu didn't give me the option to resize my existing partition? When I reformat I'll allocate space for it before installing Windows to avoid the problem.

Thanks for the input.
--Rikki

---

### Post by RikkiUW on 2009-01-30
Interesting update, I only thing I have done to fix the problem is a defrag with the windows defrag utility, and now the problem has suddenly disappeared. Any ideas?

---

### Post by skunkbad on 2009-01-31
I had an issue like this a couple days ago. I defragged XP in safe mode, and everything is fine. It's just friggin Windows! Someday we will look back and laugh at how we used it.

---

