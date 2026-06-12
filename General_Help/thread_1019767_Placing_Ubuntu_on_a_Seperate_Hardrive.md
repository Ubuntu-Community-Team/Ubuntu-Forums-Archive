---
title: "Placing Ubuntu on a Seperate Hardrive"
date: 2008-12-23
forum: General Help
---

### Post by vegatron on 2008-12-23
Hi, 
 I'm my computer has 2 hardrives, one 300gb and the other 10gb.  I'm trying to set it up so that Ubuntu/the operating system is contained to the 10gb and the 300gb will be used for just storage.  Someone told me that it would be best this way, so that in case the operating system gets corrupted or contaminated, i'd be able to format the hardrive/reload the o.s. without losing any of my files.

if there's a setup that you think would be more ideal than this please let me know!

---

### Post by Pobega on 2008-12-23
That's probably a good idea; You could also create a 10GB partition on the 300GB hard drive, and use it to back up your OS. So in the case of your 10GB hard drive dying, you could just replace it and reimage the operating system to it; it's easier than reinstalling in my opinion.

---

### Post by vegatron on 2008-12-23
wouldn't that defeat the purpose of having the second hd in there then? its a new computer, so i'm not too concerned with the 10g dying anytime soon. I know how to partition the hd, but how would I move the os to that section of the partition once i was done?  how would I make it so that files would be saved on the larger partition?

---

### Post by albinootje on 2008-12-23
> **vegatron said:**
>   I'm my computer has 2 hardrives, one 300gb and the other 10gb.  I'm trying to set it up so that Ubuntu/the operating system is contained to the 10gb and the 300gb will be used for just storage.

I think it makes sense to have /boot and / partitions on the 10 Gb drive.
And then have /usr /var /home and swap partitions on the 300 Gb drive.

The 10 Gb is probably old and slower, and by putting /usr on the new disk you will likely notice a bit of performance difference when starting applications.

---

### Post by vegatron on 2008-12-23
how would I go about setting it up like that?

---

### Post by albinootje on 2008-12-23
> **vegatron said:**
> how would I go about setting it up like that?

During the partitioning part in the Ubuntu installation you would create the partitions. 
You don't have any valuable data on this disks anymore, no ? 
Or you made backups of that ?

Here's my proposal :
10 Gb disk :
/boot/ 150 Mb
/ the rest

300 Gb disk :
/usr 20 Gb (depending on how much software you expect to install)
/var 5 Gb
swap -> 2x your RAM in Gb
/home the rest

I do recommend that after installation you make a proper backup of the 10 Gb data (For example with tar)!

---

### Post by vegatron on 2008-12-23
That sounds like it would work well for what I have in mind.  How would I go about executing that though?  I'm fairly new to linux still...I found [this page]("http://www.psychocats.net/ubuntu/separatehome") that explains how to create a new home partition using a live cd, and i'm assuming I could use these commands for the different partitions i need to create...  

thanks so much for your help!

---

### Post by albinootje on 2008-12-23
> **vegatron said:**
> That sounds like it would work well for what I have in mind.  How would I go about executing that though?  I'm fairly new to linux still...I found [this page]("http://www.psychocats.net/ubuntu/separatehome") that explains how to create a new home partition using a live cd, and i'm assuming I could use these commands for the different partitions i need to create...  

During the installation you get the chance to divide the two disk you have in several pieces.
If you look at the screenshots from the link you mentioned you can see that that is about resizing.
In your case I assume that for the 10 Gb disk you would not need that, so it's a matter of first creating a "primary" partition on the 10 Gb of 150 Mb with /boot as "mountpoint".
Then create the / partition as second "primary" partition on the 10 Gb letting it have the rest of that disk.
After that continue with the second disk.
The disks are probably gonna be recognised as /dev/sda and /dev/sdb.
If the 10 Gb is connected to the primary IDE interface, then it would be /dev/sda.
> 
thanks so much for your help!
You're welcome.

If you want, boot from the Ubuntu cdrom, and choose the try-out non-install option.
Fire up a terminal ( -> Applications -> Accessories -> Terminal),
and post the output of :
```

sudo fdisk -l
lspci
lsusb
cat /etc/lsb-release 

```
Then we can help you a bit easier with the partitioning part during the installation later on.

---

### Post by Wartender on 2008-12-23
totally unrelated but.. where on earth did you get a 10Gb hard drive? the smallest i can find is like 80 haha

---

### Post by vegatron on 2008-12-23
> **Wartender said:**
> totally unrelated but.. where on earth did you get a 10Gb hard drive? the smallest i can find is like 80 haha

The computer came with it, it originally had vista, and the 10gb was for recovery/backup

---

### Post by vegatron on 2008-12-25
I've created a live CD and i'm ready to go in and start partitioning, but i'm a bit confused by the different codes I need to enter, I don't want to leave out a step that will screw up the partitons, is there a good link that you know of that would teach me step-by-step what codes to enter in the terminal?  I want to make sure I do this properly...

I found [this link]("https://help.ubuntu.com/community/CreateBootPartitionAfterInstall") as well, its still a bit complicated though...

thanks so much for all your help!

---

### Post by albinootje on 2008-12-25
> **vegatron said:**
> I've created a live CD and i'm ready to go in and start partitioning, but i'm a bit confused by the different codes I need to enter, I don't want to leave out a step that will screw up the partitons, is there a good link that you know of that would teach me step-by-step what codes to enter in the terminal?  I want to make sure I do this properly...


Take a look here :
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

