---
title: "External Hard Drive ALWAYS Losing Data"
date: 2009-02-28
forum: General Help
---

### Post by mulligan.can on 2009-02-28
Almost EVERY time my external HDD is disconnected it suffers filesystem corruption.

If I disconnect safely by right clicking the icon in dolphin then it seems to be fine.

However just unplugging, even after waiting for all files to transfer and disk activity to cease, often causes filesystem issues. Not much most of the time.

The really big one tho is shutting down/starting up with the drive still connected! This has, one two occasions with different filesystems, caused the filesystem to get completely fragged.

First time I was using JFS and fsck.jfs couldn't fix it. Hell it barely tried. Something about journal and superblock being toast I think.

Second attempt I had the drive on XFS. xfs_check spat out a million and one errors similar to this "agi unlinked bucket 42 is 0 in ag 3 (inode=3221225472)". xfs_repair spat out "couldn't verify primary superblock - not enough secondary superblocks with matching geometry !!!" and is now searching for a secondary superblock.

I only got this drive a few days ago. Computer has only been rebooted twice in that time. Twice the external HDD filesystem has been fragged. (The drive was connected at power down and power up so not sure where the problem was introduced)

WHY ON EARTH DOES THIS HAPPEN!?!?!?!?!?

Seriously, it has me bamboozled. And this drive is pretty much useless to me if I can't have it plugged in at startup and shutdown.

Any help would be very very very much appreciated.

Thanks in advance, mulligan.

---

### Post by mulligan.can on 2009-02-28
I just unplugged the drive and let it spin down (its a maxtor 1tb deal that has its own power supply and only powers up when usb is plugged in, some funky power saving i think).

I then plugged it in again... AND IT WORKED!!??!?!?!?

xfs_check reported no errors and xfs_repair reported nothing overly amiss.

So.. I can't have the drive plugged in at boot up it appears?

Oh and on occasion I unplug the drive and then plug it in again and dmesg|tail will throw up the following a few times:

[ 2514.088771] attempt to access beyond end of device
[ 2514.088773] sdb: rw=0, want=71, limit=1

That is the result I got with the JFS partition however the JFS never fixed itself. Opening QTParted when I was using JFS reported that the partition was bigger then the max size of the disk. fdisk and parted also reported the same no matter what i did.

In the end when using JFS I had to use parted/fdisk to erase the partition table completely and start from scratch.

Oh and testdisk/photorec was NOT able to recover ANYTHING from the JFS attempt.

I am really worried about my data integrity. Is anyone able to shed some light on this?

(oh and would a mod be able to change the variant to all? I'm pretty sure this is NOT a kubuntu/kde issue)

---

### Post by mtopro on 2009-02-28
I am curious why you would be using JFS or XFS.  I have used NTFS and FAT which have issues but have been very happy with EXT3 on several powersaving external TB drives.  What is your reasoning for selecting JFS?
 
[http://en.wikipedia.org/wiki/JFS_(file_system)]("http://en.wikipedia.org/wiki/JFS_(file_system)") mentions:
> JFS journals metadata only, which means metadata will remain consistent but user files may be corrupted after a crash or power loss.

---

### Post by hikaricore on 2009-02-28
> **mulligan.can said:**
> Almost EVERY time my external HDD is disconnected it suffers filesystem corruption.

If I disconnect safely by right clicking the icon in dolphin then it seems to be fine.

However just unplugging, even after waiting for all files to transfer and disk activity to cease, often causes filesystem issues. Not much most of the time.


You should **always** unmount a filesystem before disconnecting it.

This is rule one for data safety and is the same on all operating systems..

---

### Post by mulligan.can on 2009-02-28
I do always safely unmount when removing the drive. However I was essentially stress testing it to see what degree of damage could result.

I am more worried by the apparent corruption at power up/down. That is what scares me as I will most definetly forget to disconnect it before shutdown at some point.

I chose XFS/JFS as in the past I have used them and found it to be very reliable. ext3 tends to slow down too much for my liking.

The main reason for this was that formatting the 1000gb drive to ext3 resulted in an excessively large amount of space allocated to the journal imo. it reported something like 40gb used after a fresh format and this confused me, especially as it happened a couple of times.

In the end I decided to have a stab at using JFS (mistake I think) and then XFS when the JFS prematurely gave up the ghost.

I am using ext3 on my home partition, this will most likely be changing to XFS soon. In the end, personal preference. ext3 seems like too much of a hack job to me. It's ext2 + journalling, I prefer something designed from the ground up to include it ie XFS.

---

### Post by hikaricore on 2009-02-28
At startup/shutdown your drive should be unmounted by Linux just like any other filesystem.
If you are simply turning the system off for some insane reason without shutting down then this is the cause.
Otherwise if you're losing data at this point and shutting down properly something else is likely wrong.

You should be aware that any proper filesystem will take up a certain amount of space during an initial format, this is true with NTFS, EXT4, EXT3, and EXT2.
You should also be aware that your new 1Tb hard drive is only around 931GB to begin with thanks to the industry standard in drive sizing.
Mine are between 917Gb and 925Gb after formatting.

If you want to trust your data to JFS/XFS then by all mean, but I don't suggest it.
Just because EXT3 doesn't live up to your expectations please don't assume it's a "hack job".

Everyone has their own preferences in filesystems but don't assume there's something wrong with a very sturdy and commonly used filesystem just because you don't understand it.

---

### Post by mulligan.can on 2009-02-28
Yeah, I do realise it is only about mid 900's to start with. It was reporting 45gb used straight after format. (ie 890gb free of 930gb or similiar) I wasn't expecting something so massive. Would that be normal?

I assumed that the drive would be cleanly umounted on a proper shutdown as well. However this is somehow not the case? Good to know there isn't some well known bug/fault that causes 900gb+ drives to go insane when umounted at shutdown. This is what is worrying me the most.

I didn't mean to imply that ext3 IS a "hack job" imo. Just that the concept "feels" like it. ext3 seems to have worked well with my primary partitions but I found it slowing down when the drive got nearly full.

Can you please enlighten me as to why XFS/JFS would be a bad idea? I am mainly in the testing phase of using this external drive as there is no way in hell I am trusting my data to it unless I know it is safe. Hence unplugging it without safe removal. Never thought a shutdown or start up could damage it tho.

Thanks a lot for the input so far (and for actually reading through this disjointed post)

---

### Post by mulligan.can on 2009-02-28
Hmmm... Just did some more looking...

Ext3 has better error recovery than XFS in the event of something such as an unclean dismount.

If thats true then I shall capitulate and reformat. Actually... I think I shall anyway. I don't quite trust XFS after this and JFS is definetly a no-no.

---

### Post by Slim Odds on 2009-02-28
Also note that ext3 defaults to reserving 5% of the disk for the "root" user.

You can change this at format time, or afterwards with tune2fs.

---

### Post by mtopro on 2009-02-28
My TB drives are all formatted to EXT3 and I have found it very reliable and fast.  The external drives are MYBOOKs are 924gb as formatted and also have the power save option and have been very reliable for several years so far.  My internal TB drives are WesternDigital and are 906gb.

I have not heard many experiences of JFS/XFS in use, so I appreciate your openess to share your experiences.

If you want a reliable data source, I would recommend going with something that is proven and can easily be recovered and backed up.

Also it is not unheard of to get a bad drive.  If it continues to give you issues you may want to return it while you can..  Good luck! :)

---

### Post by mulligan.can on 2009-02-28
Bleh. I have used JFS in the past, had it running my /home for 8 months without a hitch at one point.

This latest experience has soured the idea entirely for me however. Removable media just doesn't seem to like JFS/XFS.

Just reformatted using mkfs.ext3 (the original couple I used qtparted) and it's showing minimal usage after format.

ext3 held up to being unplugged without a safe umount fine.

Haha, I almost considered saying bugger it all and returning to good ol' fat32. At least file recovery is easy when it screws up.

Thanks a lot for the help guys.

I am going to stick with ext3 and pray that it was just a glitch with xfs/jfs causing the shutdown/bootup issues.

---

### Post by hikaricore on 2009-02-28
> **Slim Odds said:**
> Also note that ext3 defaults to reserving 5% of the disk for the "root" user.

You can change this at format time, or afterwards with tune2fs.

This is news to me, I found very little documentation on the -m flag however and am slightly apprehensive of using it.
Are there any performance or data integrity concerns I should be aware of with this flag?

---

### Post by Slim Odds on 2009-03-01
> **hikaricore said:**
> This is news to me, I found very little documentation on the -m flag however and am slightly apprehensive of using it.
Are there any performance or data integrity concerns I should be aware of with this flag?

I don't know of any problems. I've done it quite a few times on live partitions. Since it's just a house keeping type of thing, it should be very safe.

On large data partitions (i.e., /home), it can save a **LOT** of space.

I also partition my systems with a separate partition for /var and /tmp, so I don't really need a lot a reserved space for out of disk conditions (which is what that is really there for in the first place).

---

