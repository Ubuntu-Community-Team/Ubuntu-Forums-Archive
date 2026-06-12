---
title: "non-contiguous???????????????????????"
date: 2006-02-15
forum: Desktop Environments
---

### Post by nrayever on 2006-02-15
I've got a question in mind... when ever I boot up the filesystem check says I've 7% of non-contiguous blocks... I've read some other threads and posts and the conclusion is that it doesn't really matter... so ok... I don't have to care too much about that, but what is non-contiguous? How does it affect my system, or doesn't it?

---

### Post by towsonu2003 on 2006-02-15
I've got that "problem" as well. Mine was about 18% (1 month ago). then for some reason, it went down to 11%, than to 7% (current). No idea why / how. Doesn't cause any problems. Too much contagious space (defragmentation) may slow down the computer, but I don't think you can recognize the slowness. In this machine, there is no difference btw 18% and 7%.

---

### Post by Ocxic on 2006-02-16
there will always be a small amount of fragmentation because not all files take up all the space in a hard drive block. example: your file is 58KB if your file sytem uses 4KB blocks then 58 / 4 = 14.5  wich means that there in one 4KB block with only 2 KB of data in it, scince this spce cannot be shared with another file you get a 2KB non-contiguous 4KB block. this is nothing to worry about, and should never get bad enought to harm you system, so far i haven't heard of anything over 20%. this is not  the problem as with windows, so there is no need to defrag your drive as you would in windows, scince linux hadles it filesystem very efficently(sp?)

and after re-reading my post i'm very suprised that i even know this.... and must be the best explination of anything I've ever given. assuming I'm correct, wich i think i am.

---

### Post by towsonu2003 on 2006-02-16
[QUOTE=Ocxic]
and after re-reading my post i'm very suprised that i even know this.... and must be the best explination of anything I've ever given. assuming I'm correct, wich i think i am.[/QUOTE]
lol

From my thread about that 18%, I can say that no one around saw a 18% before... I'm gonna wipe this out with Dapper anyway ;) Anyway, it wasn't causing any problems except a very disturbing "you've got 18% non-contagious, you've got windowzed, hahaha" kinda message after fsck's...

---

### Post by dcstar on 2006-02-16
"Fragmentation" refers to how a file is logically located on a disk with respect to other files which may occupy blocks in-between the start and end blocks of a file.

For example, a file needing 10 blocks of space may occupy blocks 2345-2354 on a disk - this is "Contiguous" and is not fragmented (and the drive can read the whole file without skipping any blocks).

Another 10 block length file may occupy blocks 3001-3004, 3102-3104 & 3200-3202. This file is "Fragmented" because of the gaps, and the disk drive has to do more work to read the whole file.

Good filesystems will always try and write files in one contiguous length, but in the "real world" this is not always possible, so with ext2/3 filesystems you get a little bit of non-contiguous files.

AFAIK FAT32 just writes at the next free space from the start of the disk, so after a while any written file gets fragmented.

---

### Post by nrayever on 2006-02-16
ok, so what is non-contiguous???? i don't get it!!! what is about??

---

### Post by Leigh on 2006-02-16
"Contiguous" means thats neighbouring items share a border or a common boundary.

So, when talking about hard drives, non-contiguous means that the data relating to one file is split up over several clusters that are not touching each other, in other words, the data is fragmented. If this keeps happening with your data, eventually disk access times will increase as the head has to move and/or wait for the data to come round again in order to read it. In a contiguous space, each data block follows the previous, so the head can read all of it without moving, hnce faster read times.

HTH

---

### Post by ikd69 on 2006-03-14
Hi all.  I got similar non-contiguous messages, though this time  with 4.2% at the /home partition, the system gave a "fail" message when it completed  the disk-check... Is this an early warning that ... the end is near?

IKD

---

### Post by towsonu2003 on 2006-03-14
[QUOTE=ikd69]Hi all.  I got similar non-contiguous messages, though this time  with 4.2% at the /home partition, the system gave a "fail" message when it completed  the disk-check... Is this an early warning that ... the end is near?
[/QUOTE]
I got a fail message with 4.8% myself recently. Never worried about it, but when you say "is the end near" -> now I'm worried. You can try to check it once more using a live cd (search google for howto) or after rebooting (search the forum for how to). I will try mine using a live cd (I need to google myself ;) ) as may be doing this from terminal will give more (and correct) output.

---

### Post by JimS on 2006-03-14
...

Are we discussing non-contiguous files or
non-contiguous space??  Basically HDs are
are made up of space (empty space that is)
and files (data).

Non-contiguous files is a MS Windows problem
where files broken into parts and skattered
about the HD.  The result slows computing.

Non-contiguous space is the left over block space
where block(s) are not fully used,   The result is an
admin. number and does not relate to HD efficiency
to any significant degree.  There is no slowing.

Am I right?

[COLOR="Red"]JimS[/COLOR]
[COLOR="Blue"]Prostate Cancer Aware[/COLOR]

,,,

---

### Post by lleberg on 2006-03-15
My check was done a few minutes ago, 1.7%, I'm in the lead, right? :D

---

### Post by ikd69 on 2006-03-15
Actually, the disk checking process every 30 mounts when you start ubuntu reports  that there are both non-contiguous files and blocks.  But that is not my concern.

Apparently, my disk (a regular IDE 200GB) failed the test, and I was concerned that I may lose data.  I don't know why, but I have changed disks in this box several times.  

The box is and AMD64 3000+ with an ASUS SLI mobo.  Initially, there was a 200GB SATA which failed regularly every 40 days.  The dealer changed the disk twice, then changed both disk and mobo.  Last November, he changed disk, mobo, and power supply.  That was when I bought the IDE and added to the setup.

I must be headed for the guinness book of records for changing disks so many times.

IKD

---

