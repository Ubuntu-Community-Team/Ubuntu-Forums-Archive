---
title: "Checkdisk, Defragger etc.. for Ubuntu?"
date: 2009-06-15
forum: General Help
---

### Post by Gp. on 2009-06-15
After switching from windows, I need some defragging and disk checking tools for Ubuntu.

What can you recommend?
Suggesting other useful system maintenance tools also welcomed XD

---

### Post by Gen2ly on 2009-06-15
Ubuntu by default uses the ext3 filesystem.  The filesystem includes support of making files continuous (not split on the hard drive), journaling (so data doesn't get lost), and performs checks on the filesystem at intermittent intervals (usually around every 30 boots).  For the most part: you're good, nothing much to worry about.  There is a command that can force checks on the disk on boot but at the time I'm on a Windows pc and just don't remember what it is. :)

---

### Post by johnsd on 2009-06-15
> **Gp. said:**
> .., I need some defragging.

The user does not need to get involved with defragging in Linux - the system does this as it is working as I understand it.

---

### Post by Gp. on 2009-06-15
Well 2 of my drives use NTFS...
So defragging for those.

Also I still need a drive checker (errors etc..)

---

### Post by Gen2ly on 2009-06-15
Disk checking, read two posts above. :)

---

### Post by johnsd on 2009-06-15
The need for defragging is much less with NTFS compared to FAT systems - not sure if it is worth being concerned about?

---

### Post by Gp. on 2009-06-15
> **Dirk.R.Gently said:**
> Disk checking, read two posts above. :)

Yeah I know, but thats for ext3 not NTFS yeah?
I need to check my NTFS drives for errors like damaged sectors etc..

---

### Post by Celauran on 2009-06-15
Defrag the NTFS disks from within Windows if you're worried about it. That's the only conceivable reason you'd have NTFS anyways. Linux's checkdisk is called fsck and, as mentioned, runs automatically about every 30 boots.

---

### Post by chriskin on 2009-06-15
it seems to me that you don't need to care about those things any more

you came to the linux side, let the system do its work and just relax :)
i have linux systems almost 3 years now and none of them has shown any problem of fragnentation, so the system must be taking care of ntfs as well

or i just missed the signs of fragmentation :P

---

### Post by nikhilk on 2009-06-15
> **Gp. said:**
> 
I need to check my NTFS drives for errors like damaged sectors etc..

I have not heard of such a (production ready) tool for Linux. Since NTFS is a proprietary M$ format, such tools are not easy to develop for Linux. It is usually assumed that you can defragment from the Windows installation that you created the NTFS drives.

---

### Post by 3rdalbum on 2009-06-15
The last I heard, the NTFS-3G team was thinking of doing an "fsck.ntfs". But, think about it: NTFS-3G can't safely handle drives that have not been properly unmounted. What are the chances that they can safely repair errors in NTFS filesystems?

If you want to check your NTFS drives for errors, or defragment them, you need to boot into Windows. If you don't still have Windows, then what are your drives NTFS for?

---

### Post by Gp. on 2009-06-15
> **Celauran said:**
> Defrag the NTFS disks from within Windows if you're worried about it. That's the only conceivable reason you'd have NTFS anyways. Linux's checkdisk is called fsck and, as mentioned, runs automatically about every 30 boots.

I use linux primarily now.
The problem is my 2 storage drives use NTFS.
How am I supposed to change them to ext3? I've got nowhere to put all that data so I can format to ext3, which is why they are still NTFS from when I was using windows.

Any ideas?

---

### Post by Celauran on 2009-06-15
Really, no. Linux can't defrag/checkdisk NTFS drives.

---

### Post by nikhilk on 2009-06-15
> **Gp. said:**
> I use linux primarily now.
The problem is my 2 storage drives use NTFS.
How am I supposed to change them to ext3? I've got nowhere to put all that data so I can format to ext3, which is why they are still NTFS from when I was using windows.

Any ideas?

There is no utility to do an in-place conversion of NTFS filesystem to ext3.
Take a look at [this]("http://www.linuxforums.org/forum/linux-newbie/52309-changing-ntfs-ext3-without-losing-any-data.html"). Maybe you can do something similar?

---

### Post by Cheesemill on 2009-06-15
Just reformat the drives as ext3 then restore all the data from your backup :)

---

### Post by babavwoko on 2009-06-15
Linux does not need those cos it uses journaling files system and if you insist you must check your ntfs drives which IMHO doesnt have problems like fat. Use Gparted it can check ntfs and fat for errors

---

### Post by sedawk on 2009-06-15
I agree that some repair and defrag tool would be really nice
for Linux, especially if you repair the PC of some poor XP or Vista
user from a save and clean Ubuntu Live CD!

The worst thing about Windows is the freakingly slow defrag tool.
With 2 and more GB or memory it should be possible to cache much
more data into memory before writing it to disk again.
There are tools to defrag single files (e.g. contig from SysInternals),
but a nice Linux high performance defragger (working on unmounted
NTFS file systems) gets a Top-5 entry of my most-wanted list.

For now, you need windows to repair and defrag NTFS. If you
do not have installed Windows anymore have a look at "BartPE".
(Bootable Windows Rescue Disk)

---

### Post by Gp. on 2009-06-15
> **Cheesemill said:**
> Just reformat the drives as ext3 then restore all the data from your backup :)

Can't, got no spare space for a backup.
Guess I'll have to buy a few more drives.

---

### Post by krackedpress on 2009-08-27
> **Gp. said:**
> Can't, got no spare space for a backup.
Guess I'll have to buy a few more drives.

What happens with people who do not have the spare drives or money to buy them?
I took my 3 drive file server and made it a linux box.  ALL of my file on the two drives not converted to ext3 when ubuntu was installed are needed and must be kept.  I did not have room to make the first drive a dual boot one and the two other drives are stuffed full.

So tell me how do I defrag the two SCSI NTFS formatted drives using linux only?

It will be a big problem soon, since I NEED to defrag the drives every month or so.

---

