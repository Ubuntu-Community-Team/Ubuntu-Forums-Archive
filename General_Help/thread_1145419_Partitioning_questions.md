---
title: "Partitioning questions"
date: 2009-05-01
forum: General Help
---

### Post by alms66 on 2009-05-01
I would like to install Vista 64 and Ubuntu 64 on the same computer.  I have Vista installed already, in fact.  From what I've read so far, this is the way to go, install Vista then Ubuntu.  I also want to have a shared dataspace between the two OS's, so I can acess my media and documents regardless of what I boot into.

I have a 750 GB hard drive.  How would you recommend I go about partitioning this thing out?  Can I get people's opinions on this and most importantly, reasons why you say to do something different.  Anyhow, I was thinking of doing this:

Vista - 100
Data - 500
Ubuntu - 100
Swap - 5
Unpartitioned - 45*

*I read that it's a good idea to leave some unpartitioned space in case there is a need to resize in the future.

---

### Post by codeseer on 2009-05-01
> **alms66 said:**
> 
Vista - 100
Data - 500
Ubuntu - 100
Swap - 5
Unpartitioned - 45*


That looks pretty good to me. I'd say change the swap to equal the amount of RAM you have though; that's the general standard, though you might not ever use over 1 GB.

---

### Post by arepaking on 2009-05-01
> **alms66 said:**
> I would like to install Vista 64 and Ubuntu 64 on the same computer.  I have Vista installed already, in fact.  From what I've read so far, this is the way to go, install Vista then Ubuntu.  I also want to have a shared dataspace between the two OS's, so I can acess my media and documents regardless of what I boot into.

I have a 750 GB hard drive.  How would you recommend I go about partitioning this thing out?  Can I get people's opinions on this and most importantly, reasons why you say to do something different.  Anyhow, I was thinking of doing this:

Vista - 100
Data - 500
Ubuntu - 100
Swap - 5
Unpartitioned - 45*

*I read that it's a good idea to leave some unpartitioned space in case there is a need to resize in the future.

You initial structure looks good to me. I think you are good to go. I would recommend to format "DATA" partition into NTFS so both OS can see it.

As a side note you may want to have /home in a separate partition, it would help a lot if you need to restore your system in the future.

Good Luck!
-AK

---

### Post by perrti-y02 on 2009-05-01
I agree with arepaking about separate home partition. I don't mean to belittle you or anything but chances are, if you try to experiment, something WILL go wrong and a reinstall will be needed. I have done it so many times. It's all part of the fun!!!!

I usually partition shared data partitinos as FAT32 but Ubuntu accesses the data very slowly. Don't know if this is only for FAT32 or if it is anything this isn't ext.

Have fun

---

### Post by lisati on 2009-05-01
Looks promising. As has already been noted, things can sometimes go wrong - so don't forget to make a back up of your important data, this includes recovery paritions if you so choose.

---

### Post by Paqman on 2009-05-01
> **alms66 said:**
> 
Vista - 100
Data - 500
Ubuntu - 100
Swap - 5
Unpartitioned - 45*


You might want to include at least one of those four partitions inside an extended partition. If you don't create an extended partition at this stage you won't be able to create any more partitions in the future.

Ubuntu runs perfectly well inside an extended partition, but i'm not sure whether Windows would do likewise.

---

### Post by amtnbiker16 on 2009-05-01
on a side note, make sure whatever partition you want to extend in the future is right next to the free space, probably with the free space at the end of it, or you wont be able to extend that partiiton later

---

### Post by alms66 on 2009-05-01
Ok, so based on the feedback...

Vista - 92 (NTFS)
Ubuntu - 20 (ext4)
Home - 80 (ext4)
Data - 500 (NTFS)
Swap - 8

As far extended partitions, I've read that Windows will not run on an extended partion.  Can I set all of these as primary except for the last two?  I don't know if swap has to be on primary off-hand...
I'll drop the free space idea if you can't extend any partition using that - seems pointless then.

Do you think 20 is large enough for Ubuntu?  I can make it larger, stealing a bit from the data partition.

And thanks everyone, that was a quick and thorough reply!

---

### Post by alms66 on 2009-08-22
Ok, so I finally got around to doing this...

EDIT
Nevermind.  I didn't have the option during the Ubuntu install to format the data partition as NTFS, which I simply assumed I would.  However, I loaded up the liveCD after installing Vista then Ubuntu and used the partitioning tool there (Gparted - IIRC) to format the drive to NTFS, which took all of 10 seconds...
Why wasn't I just given that ability during install?  That would have made things a bit more simple.  Perhaps I missed how to do it correctly, but I just recall seeing FAT16 and FAT32, no NTFS.

---

