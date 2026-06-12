---
title: "Does Ubuntu reorganize files and free space automatically?"
date: 2009-02-08
forum: General Help
---

### Post by susanne260 on 2009-02-08
I installed Ubuntu in November last year, and since that time I've been copying many files onto my 500GB HDD. I bought an another HDD when the first one had just 100GB of space left. Then I copied almost all of the stationary multimedia files from the first HDD to the second.

But here's the thing: since I installed Ubuntu in October last year, I have also been installing a lot of programs during that time. So I'm assuming that those programs on my first HDD are now scattered all accross the drive and there are big chunks of free space between them.

Is there a way to neatly reorganize all the files that are scattered on the disk to the start of the disk? I mean just like when Ubuntu was first installed. Because at the moment I'm assuming the drive head has to constantly jump from the beginning of the drive to the end.

---

### Post by Gorgapor on 2009-02-08
No, but it's not a problem like on FAT32 filesystems

[http://en.wikipedia.org/wiki/Ext3#Defragmentation](http://en.wikipedia.org/wiki/Ext3#Defragmentation)

---

### Post by susanne260 on 2009-02-08
Well, yes... the files may not be fragmented, but they're still scattered all over the HDD. And the drive head has to constantly jump from the beginning of the drive to the end, which affects the performance and also shortens the HDD's lifespan...

I guess I'll have to wait until Ext4 is implemented in Ubuntu. At least that has something that might do the job. I don't know how you guys have managed without such a critical component for so long. :confused: :D

---

### Post by mb_webguy on 2009-02-08
The ext3 filesystem minimizes fragmentation, so defragmentation isn't really necessary.  Generally, files will only start to become fragmented when the filesystem approaches full capacity, and the system has to fit files wherever it can find the room.  For most ext3 filesystems, this means that you can use the filesystem continuously for years without worrying about fragmentation.

As an example, I have three ext3 partitions on my computer.  One is used as my /home directory, and is only 2GB.  The second is my / partition, is 12GB, and was reformatted about a month ago when I changed from 32-bit to 64-bit Ubuntu. The third is for data storage, and is 115GB.  The /home and data partitions have been in continuous use for about two years.  I'm currently using about half of the available space on each of the three partitions.

Running "sudo e3fsck -n" on these partitions shows that my / partition is 0.8% fragmented.  This actually seems like quite a bit to me considering that I just reformatted the drive a month ago.  On the other hand, it's a relatively small drive, and I have used more of the drive than I currently am, such as immediately after I installed the new version of Ubuntu, and downloaded the 200+ package updates.  

My /home partition is currently the most fragmented at 10.8%, which I expected, since I've been using this partition for two years, and a couple of times during this period I accidentally filled up the partition completely.  

My data partition isn't fragmented *at all*, even though I've been using it just as long as my /home partition, because it's never been more than about 90% capacity.

---

### Post by susanne260 on 2009-02-08
Thanks for the reply, but it isn't really the fragmentation that I'm worried about. The space on my first HDD is now 95% free, since I copied all the multimedia files to the second HDD... but the problem is that those 5% of files are scattered all over the HDD, even though 95% is free space.

I'm looking for a way to "push" those files together to the beginning of the HDD, so the drive head doesn't have to jump all around the plate any more.

---

### Post by jrusso2 on 2009-02-08
> **susanne260 said:**
> Well, yes... the files may not be fragmented, but they're still scattered all over the HDD. And the drive head has to constantly jump from the beginning of the drive to the end, which affects the performance and also shortens the HDD's lifespan...

I guess I'll have to wait until Ext4 is implemented in Ubuntu. At least that has Online Defragmentation. I don't know how you guys have managed without such a critical component for so long. :confused: :D

The same way Microsoft used to say NTFS did not need defragmenting for many years.  People believe what they are told.

---

### Post by susanne260 on 2009-02-08
Oh gosh... I regret that I ever used the word "fragmentation" in this thread. It started a discussion in completely wrong direction... :D

---

### Post by mb_webguy on 2009-02-08
Well, one option (and probably your best one) is to copy all of those files to another partition or to external storage, reformat the partition, and copy the files back.

There is a defragmentation tool available for ext2 called e2defrag which can also be used for ext3 (by converting the ext3 partition to ext2, which doesn't require reformatting), but doing so can result in data loss.

---

### Post by susanne260 on 2009-02-09
> **mb_webguy said:**
> Well, one option (and probably your best one) is to copy all of those files to another partition or to external storage, reformat the partition, and copy the files back.

Yes, I was afraid of this being the only safe way of doing it with Ext3... oh well. Thanks for confirming it!

Thanks everyone for helping me out! :)

---

### Post by TheUnderTaker on 2009-02-10
Ext3s block allocation does minimize Fragmentation. Ext3 is broken up into 128MB block groups and it really depends on the fragmentaton of the block groups as ext3 dosent look for free space for the exact size since the kernel allocates 4KB blocks one at a time.

---

### Post by boof1988 on 2009-02-10
> **susanne260 said:**
> I'm looking for a way to "push" those files together to the beginning of the HDD, so the drive head doesn't have to jump all around the plate any more.

Aren't modern HDDs composed of several platters (please correct me if I am wrong here)?  If that is the case, then how can one be sure that the head(s?) on a single platter jump between the beginning and end of that platter?

---

