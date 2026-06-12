---
title: "Defragment an NTFS HD before installing XP?"
date: 2009-02-09
forum: General Help
---

### Post by NuttyMonk on 2009-02-09
Hi all,

i have an NTFS hard disk (not my main one which has Ubuntu on it) which i want to install Windows XP on for a dual-boot.  It was formatted and used when i used Windows XP as my only OS.

Is it necessary (advisable) for me to defragment it before partitioning it?  I guess that if it's fragmented and i partition it then the Windows XP OS which i install on that partition could be physically spread over the whole hard disk.  If i defragment it first then the partition which i create for the Windows install would be contiguous.

Does that sound right?

If so, how can i go about defragmenting the hard disk in Ubuntu so all of the files which are currently on the disk are contiguous, say at the start of the disk, and i can then install Windows XP on a contiguous partition which makes up the rest of the hard disk.

Cheers

NM

---

### Post by spinanicky on 2009-02-09
No need to defrag.. just part and install it!

---

### Post by NuttyMonk on 2009-02-09
But say i create a partition which uses all of the available space on the hard disk and the disk is fragmented, won't that mean that the new partition is also fragmented by default?

Or is it the case that when you create a new partition (i'm talking about in the windows setup here) that all of the existing files on the hard disk are moved to a contiguous space on that hard disk to make way for the new partition?

Thanks for the quick response Spin

Cheers

NM

---

### Post by HavocXphere on 2009-02-09
Fragmentation occurs *within* a partition. A single partition can't get fragmented.

---

### Post by NuttyMonk on 2009-02-09
say this is the current state of the hard disk...


1000101011001110101010001101010101001010101010100101010010110

... 1's are data, 0's are empty, and i create a new partition on that hard disk.  How does the new partition get created when the existing files are spread all over the disk?  Surely a new partition must get created in the spaces and therefore the areas that the new and old partitions exist in are not contiguous.

Or am i just being kinda dense and not understanding this all correctly?

Cheers

NM

---

### Post by spinanicky on 2009-02-09
A partition says "I exist between head 1 and head 500000" (for example) so everything gets written in-between them. Your second partition will start after that. ;)

---

### Post by NuttyMonk on 2009-02-09
> **spinanicky said:**
> A partition says "I exist between head 1 and head 500000" (for example) so everything gets written in-between them. Your second partition will start after that. ;)

But my existing partition encompasses the whole hard disk from start to finish.

---

### Post by HyRax on 2009-02-09
> **NuttyMonk said:**
> say this is the current state of the hard disk...


1000101011001110101010001101010101001010101010100101010010110

... 1's are data, 0's are empty, and i create a new partition on that hard disk.  How does the new partition get created when the existing files are spread all over the disk?  Surely a new partition must get created in the spaces and therefore the areas that the new and old partitions exist in are not contiguous.

Or am i just being kinda dense and not understanding this all correctly?

Cheers

NM

Irrelevant - what matters is the partition information, not the current arrangement of the 1's and 0's on the drive. If you create a new partition, then the old data is automatically overwritten.

ie: If you already have a fragmented drive, and then you re-partition the drive, all that data is lost, and the fragmentation then becomes irrelevant because you're overwriting it with new data, not preserving the existing data.

Besides that, the default practice for installing Windows is to format the destination partition, so it's all going to be wiped anyway.

---

### Post by NuttyMonk on 2009-02-09
> **HyRax said:**
> the default practice for installing Windows is to format the destination partition, so it's all going to be wiped anyway.

So if i have a partition which covers all of a hard disk, i can't create a new partition with the empty space and keep my existing files on the existing partition?

---

### Post by spinanicky on 2009-02-09
Yes you can... but at the top you said you had formatted it?! Use disk magic or a simmilar program and it will do everything for you

---

### Post by NuttyMonk on 2009-02-09
> **spinanicky said:**
> Yes you can... but at the top you said you had formatted it?

Sorry, i didn't mean to confuse the issue.  i was just pointing out that when the disk was formatted back before i started using it, it was done with Windows XP, in case that made a difference to how the partitioning worked or the file system i used.

---

### Post by HyRax on 2009-02-09
> **NuttyMonk said:**
> So if i have a partition which covers all of a hard disk, i can't create a new partition with the empty space and keep my existing files on the existing partition?

You cannot create a new partition if there is no space to create it. If you already have one giant partition occupying the entire drive, you will need to delete or re-size it before you can add another partition.

To preserve existing files on the drive, you want to re-size the existing partition to a smaller size to make space for the new partition. You should ideally have a backup of any important data before proceeding with this. Since you are preserving data instead of wiping it, it is a very good idea to defragment the volume BEFORE you re-size it, otherwise resizing can take an ice age or two to complete because it has to shuffle too much data around in order to preserve it all.

---

### Post by NuttyMonk on 2009-02-09
Thanks HyRax.  That's what i needed to know.

So can i resize the partition using Ubuntu (assuming i defragment it first of course)?  I remember seeing that kind of stuff when i installed Ubuntu which must mean that the software/package to do it is also in the Ubuntu OS somewhere.

Thanks for your replies both of you.  Got a clearer understanding of the subject now.  :-)

Cheers

NM

---

### Post by HyRax on 2009-02-09
On the Ubuntu LiveCD, GParted (aka "Partition Editor" under System->Administration) can do the resizing manually for you if you don't want to do it via the installer.

---

