---
title: "Need advice asap before I do something even more stupid... (disk and partitioning)"
date: 2009-06-19
forum: General Help
---

### Post by itix on 2009-06-19
Hi. 

I need some help with my external disk that I have formatted as reiserFS (it was a mistake. I had the intention of making it ext3 when I formatted it many months ago, but I must have accidentially selected murderFS instead).

I was transferring a file from the external disk to a USB drive when I got an I/O error. I thought that the file system might be damaged so I ran an [COLOR="Navy"]fsck[/COLOR] on the disk (it later turned out that the USB drive was full). The fsck called for a command with the alias [COLOR="Navy"]reiserfsck[/COLOR] which did some checks and told me that it had found an error and that I should run [COLOR="Navy"]reiserfsck --rebuild-tree[/COLOR] to correct this. Great, I thought, I'll do just that. 

It started nicely with asking me if I really wanted to do this, and I replied yes, thinking this would take the same amount of time that ext3/4 correcting would take. Boy, were I in for a surprise, when the console told me that it had an immense amount of block left to check and that it did in such a slow pace that it would take two days to do this. I thought "what the hell, I'll just leave it in for two days then (and why the hell didn't you tell me that this would take two days?)"

The computer then froze all of a sudden ("no recovery"-froze -> hard kill and baaaad feelings about how the external disk would feel when the system was booted up) and now the drive won't respond. I thought of doing another [COLOR="Navy"]reiserfsck --rebuild-tree[/COLOR] (since the [COLOR="Navy"]reiserfsck[/COLOR] I ran told me that the rebuild-tree did not finish... no kidding?).

What should I do? I have veeeeery valuable data on that disk (and I am soooo going to move it all to my laptop hard drive and reformat that disk if I'm able to save it). 

Is there some way to save it in less than 2 days? Is there some way to save it at all??

---

### Post by merlinus on 2009-06-19
You might try testdisk or sysrescuecd.

---

### Post by itix on 2009-06-19
I hope none of them are big, because I'm on a ship right now with a very slow internet connection.

What will they do to the disk? That "sysrescuecd" sounds like something you might want to try on ubuntu itself.

Note please that it is not ubuntu or linux that is damaged but my external disk.

---

### Post by itix on 2009-06-19
Accidential double post (probably because of slow connection)

---

### Post by merlinus on 2009-06-19
testdisk will find and try to repair damaged or deleted partitions, and then restore the files. neither are linux-specific, and are small downloads.

---

### Post by itix on 2009-06-19
Thanks. I'll try that testdisk.

Thank you for your quick reply. I'll report the progress here later on.

---

### Post by itix on 2009-06-19
You wouldn't happen to know how you can "rescue" a partition with testdisk?
I can only find test options...

---

### Post by ad_267 on 2009-06-19
This might help: [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Testdisk is pretty good at recovering a deleted partition. If the partition is there but the data is all gone, you could try photorec. Have a look here for more recovery software: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by itix on 2009-06-19
ooooh... It seam to have found the missing partition... I hope everything is OK with it.

Thanx for the step by step guide, it reeeaaaly helped :)

I'll post back if I have any problems (unless the internet connection dies down on us again).

---

### Post by itix on 2009-06-19
Damn... It didn't work. It detects the partition correctly and everything seams in order (except the fact that I can't list any files on it because "it was not enabled during compilation"... thanx a lot), and I change the partition from deleted to primary, but it still won't mount it and nautilus still says "mount: operation not supported". When I check with the program again, the partition is bootable primary.

It seams like I have to go with the two day option after all (unless somebody magically finds a way). Thanx for trying both of you.

---

### Post by merlinus on 2009-06-19
What commands did you use to try to mount the recovered partition?  

As for testdisk, my understanding is that once the partition is discovered, you have to copy its files to another specified place from the original location, one at a time.

---

### Post by itix on 2009-06-19
Uuuuhm... after a bit of thinking, I've realised that I have based all this on a miscalculation from my side. I forgot to divide by 60 two times, so i got minutes and converted them to days (by dividing it by 24). It will just take a little over an half an hour to correct the disk.

I'll let the reiserFS disc tool work and just hope and pray. I think it is the partition itself that is damaged rather than the partition table. I think I damaged it when the first tree rebuild failed after the crash.

The commands I used was [COLOR="Navy"]analyze[/COLOR] and [COLOR="Navy"]Deeper Search[/COLOR] and then [COLOR="Navy"]Write[/COLOR] like the guide said. 

I'll see if things work out now. Sorry for the trouble I caused :(

**EDIT**: oh sorry, the commands for mounting? [COLOR="Navy"]sudo mount /dev/sdb1 /media/apa/[/COLOR] ... like always. Returned "operation not supported". So did nautlius when I clicked the disk there.

---

### Post by merlinus on 2009-06-19
Sometimes specifying the file system can help with mounting.

e.g. sudo mount -t ext3 /dev/sda1 /mnt/sda1

But you probably already knew this...

---

### Post by itix on 2009-06-19
Actually, I didn't. If I still have problems after the reiserfsck-tool is finished, I'll try with that. Thank you.

---

