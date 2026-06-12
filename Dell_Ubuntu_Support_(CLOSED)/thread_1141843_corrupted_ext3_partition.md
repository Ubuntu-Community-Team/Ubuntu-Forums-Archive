---
title: "corrupted ext3 partition"
date: 2009-04-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by repomanz on 2009-04-28
Greetings folks.

I'm hoping some folks could provide input into my grasp at a plan to save my data drive. 

The starting blocks (outter edge of platter) 60800 to roughly 95000 have ECC errors. Thus I am unable to get to any of this data nor mount it.  When seeking data during the range of blocks above, i get clicking etc.  Once out of that range, the drive reads fine with no errors.

I'm not able to mount this drive.  Trying to mount it it will tell me that i have to specify a filesystem type. This message leads me to believe that the disk that has ECC errors also now contains my badly corrupted ext3 partition information.

My plan:

I have a new drive in place and I'm copying data using ddrescue over to the new drive:

/dev/sdb  << bad drive
/dev/sdc  << new drive

sudo ddrescue /dev/sdb /dev/sdc /home/ddrescue.log

I believe this will copy even the bad partion info to the new device however preserving the image of the disk.  During my initial investigations using fsck the drive the utility told me that it couldn't read the block and also bad magic number (i don't recall the exact message).

I read online that i can use:
> There are backups of the superblock located on several positions and we can restore them with a simple command. Backup locations are: 8193, 32768, 98304, 163840, 229376 and 294912. ( 8193 in many cases only on older systems, 32768 is the most current position for the first backup )

Now, suppose you get a ¨Damaged Superblock¨ error message at filesystem check ( after a power failure ) and you get a root-prompt in a recovery console, then you give the command:

# e2fsck -b 32768 /dev/hda5

Once this data has copied i plan to try to repoint/repair my bad superblock info to a backup location area (i.e. 32768).

If this doesn't work, then i will try to fix it via testdisk (advanced tools, superblock).

Besides the obvious suggestion "why didn't you backup your data?" does anyone have any other tips to help guide me through this mess?

Thanks,

J

P.S. Two drives being delivered tomorrow for mirroring so i never run across this problem again!

---

