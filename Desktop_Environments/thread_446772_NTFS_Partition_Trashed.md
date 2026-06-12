---
title: "NTFS Partition Trashed"
date: 2007-05-17
forum: Desktop Environments
---

### Post by wallabeex on 2007-05-17
I know there's warnings throughout the Wiki about the possibility of this happening, but I figured I'd post on here and see if anyone has any solutions to rectify the problem:

I had Windows XP installed with NTFS on my primary drive, which took a solid 50 gigs of space out of my 100 gig drive (to be clear, the whole drive is one NTFS partition).  I decided to try Ubuntu, and after reading the Wiki, went through the install procedure.  When I came to resizing the partition (sorry, this is all a little vague as it was yesterday, I'm hoping the true Ubuntu Veterans can read through this haziness), I chose something like "manual" and then resized the NTFS partition.  It told me it would need to check something before I could select a new size for the drive, and I clicked "Forward" at which point it started to resize the partition only to Error out and send me back to the original partition screen. 

I read on the forums for a while and noticed someone saying that Ubuntu won't like NTFS partitions and you should really resize as EXT3, so I chose EXT3 under manual and tried a resize.  It sat for a while again and errored out again, but this time when it sent me back to the partition screen, my drive was no longer NTFS with 45 gigs free.  It was EXT3 with 100gigs free.

It appears my drive has been wiped clean and XP is lost and gone forever.  I had backed up most of my important documents before doing this but DID lose my Thunderbird e-mail.  I've been using programs like "GetDataBack" which has allowed me access to some of my files but not the ones I want.  Anyone have any suggestions before I give up and just install the system straightforward?

Thanks.

---

### Post by Psicolonia on 2007-05-17
my advice. go to a data recovery company. give them your hard drive and pay for your data if really is important.

you have, i guess from the description, formated your entire hard drive to ext3. it doesn't get any worst than that! i say again: you FORMATED THE HARD DRIVE! It's wiser to minimize data loss to do what I said. If data is important to you. If it ain't... forget the partion with XP it's gone and clean!

You can try the software you've got but once it's formated it'll be hard to get what you want. only by luck

hope it helps!

---

### Post by wallabeex on 2007-05-17
in the grand scheme of data recovery formatting the hard drive isn't the worst it gets.  i wasn't sure if anyone had any tricks on here they'd used for the same scenario, but if not then i guess what i've got is what i've got.  the data isn't worth $1000, but it's definitely worth an hour or two.  just a few resume's and coverletters.

---

### Post by sternobread on 2007-05-18
Based on what you've said, I think you're more or less hosed. The big question is did it in fact write and ext3 filesystem over your entire hard drive. If it did not, there may be potential for hope. I'd recommend booting to the ubuntu live environment and using fdisk to examine the partition table on the drive. What I would then try, is clearing the existing table and creating a new NTFS patition (I believe the type is 7 in fdisk), for the entire drive. This will NOT destroy any data on your drive, it will simply rewrite the data that points to what partition is where on the disk. The theory here is that creating an ext3 filesystem is not 
"necesarily" an entirely destructive operation. I have a feeling that the steps above would not allow you to simply re-mount your old drive as you had once known it, because the NTFS superblock was probably overwritten by an ext3 one. But it may allow you to use some type of NTFS recovery tool on it to bring somthing back. Remember the ext3 creation simply writes small blocks of data across the parition, and does not "wipe" the drive in its entirety. 

Good luck. I feel your pain.

---

