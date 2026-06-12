---
title: "windows won't boot after repartitioning. (hal.dll)"
date: 2009-04-03
forum: General Help
---

### Post by jakupl on 2009-04-03
I juggled a bit around with my partitions, and now when I try to boot windows, I get (windows root>/system32/hal.dll The file is missing. Install a copy of the file.).
I have tried to follow [this post]("http://ubuntuforums.org/showthread.php?p=4639948") (ubuntuforums), but it does not work. I know why it does not work, the attached picture explains a bit, but what partition number is windows then? I have tried with 3,4,5,6,7 and 8.

EDIT: though, when I tried 7, I got another error message, something about "Windows can not boot because of a computer disk hardware corruption..."

---

### Post by meierfra. on 2009-04-03
[size="7"]2[/size]

---

### Post by damis648 on 2009-04-03
What happens when you look at the properties of the windows partition, my attention can't help but be attracted by the warning exclamation point.

---

### Post by 3Miro on 2009-04-03
Happened to me once long time ago. It came down to editing boot.ini, however, I cannot remember how it worked. I guess you can try/error to see. I don't know about the corrupt error message, it doesn't sound good. You did back up everything important, right.

---

### Post by meierfra. on 2009-04-03
> I cannot remember how it worked.

Windows counts the partitions in the same order has linux:  /dev/hda1 , /dev/had2, /dev/had3, ....  But in contrast to linux, Windows does not assign any number to extended partition. So Windows leaves out the extended partition /dev/hda2. So Windows counts

/dev/had1    /dev/had3 ...


This makes the Windows partition (/dev/had3) the second partition. So the correct entry in "boot.ini" is 

partition(2)

> my attention can't help but be attracted by the warning exclamation point. 
> I don't know about the corrupt error message, it doesn't sound good.

Most of the time  the yellow warning sign is harmless. I wouldn't worry about it until after your tried "partition(2)"

---

### Post by jakupl on 2009-04-04
> **meierfra. said:**
> [size="7"]2[/size]

rofl!

That worked, but now for some reason, Windows freezes at login. I just get the blue screen where you usually log in, but there is nothing except a windows logo, so I need to force shutdown.

---

### Post by meierfra. on 2009-04-04
I suggest a run a file system check. Boot from your Windows CD,  press "r" to go the the repair console and type

```
map
```
This will tell you the drive letter of your XP partition
Type


```
fixboot C:
chkdsk /r C:
```
but replace " C:"  by the  drive letter of your Windows partition.

Run "chkdsk /r C:" has often as it takes, that is until is does not detect any more errors.

---

### Post by jakupl on 2009-04-05
> **meierfra. said:**
> I suggest a run a file system check. Boot from your Windows CD,  press "r" to go the the repair console and type

```
map
```
This will tell you the drive letter of your XP partition
Type


```
fixboot C:
chkdsk /r C:
```
but replace " C:"  by the  drive letter of your Windows partition.

Run "chkdsk /r C:" has often as it takes, that is until is does not detect any more errors.

Well I have reinstalled windows now. But thankyou.

---

### Post by meierfra. on 2009-04-05
> I have reinstalled windows now. 
Well, that's a sure way to solve the problem.

> juggled a bit around with my partitions, 
Just curious. What partitioning tool did you use?

---

### Post by jakupl on 2009-04-06
> **meierfra. said:**
> Just curious. What partitioning tool did you use?

gparted. the windows partition was not fragmented at all, and everything worked as it should. I did not detect anything unusual.
But maybe something bad happened anyway to the windows partition.. who knows?

---

