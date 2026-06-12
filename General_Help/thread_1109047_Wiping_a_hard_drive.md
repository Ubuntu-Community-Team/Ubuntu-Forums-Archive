---
title: "Wiping a hard drive?"
date: 2009-03-28
forum: General Help
---

### Post by mahela007 on 2009-03-28
HI everyone. 
One of my friends has a windows PC and has somehow managed to load it up with viruses. So it's up to me to save the day. Can I use the partitioning tool on the ubuntu live CDs to completely wipe the hard drive? (That's what he wants to do.)

And also I would like to know if there is a parition manager installed by default on kubuntu.

PS: I think is a great opportunity to convert another windows user to linux :twisted: 
;)

---

### Post by tanzoniteblack on 2009-03-28
You can use it to delete the partition, which is normally good enough to prevent any viruses from surviving the reinstall you do afterwards.  It's the option I would recommend.

DANGER WILL ROBINSON: And if you want to securely delete everything on the disk permanently and completely you could use a free program such as DBAN ([http://www.dban.org/](http://www.dban.org/)) to write over the filesystem multiple times to make nothing on the disk recoverable...ever. 
**It will delete everything on every disk connected to the computer.  So only use this option if you really need it.  Try the other option first.**
DANGER WILL ROBNINSON!

Keep in mind though that all of these options will destroy all the data on the partition (and DBAN for every partition on the entire disk and on every disk hooked to the computer), which might be what you want...just make sure that really is what you want before you do it, because once you do there's no going back.

---

### Post by mahela007 on 2009-03-28
I dunno about DBAN. However I am certain that what my friend (and I) wants is to format the disk. Does anyone know about a default partition editor on KUBUNTU?

---

### Post by Bucky Ball on 2009-03-28
DBan destroyed everything on the disk when I used it and it took a lot of screwing around to get it up again. It had no ID whatever left. Nothing would recognise that disk, and I mean nothing. Couldn't even reformat. I wouldn't advise unless you know exactly what you are doing, and I will agree: DANGER WILL ROBINSON!

---

### Post by tanzoniteblack on 2009-03-28
I believe that Kubuntu comes with qtparted.  You can find out if you're using the 8.10 disc by booting it up, going to the kmenu and doing a search with just typing "part" and seeing if anything mentioning partition editor or something similar arises.
If not and you're on the internet you can install programs even when running from a live CD, just go to the add/remove programs manager (adept or add programs in Kubuntu, I think) and install gparted or qtparted.  You can use either of these partition editors to delete/reformat a partition.  I generally find that gparted will read the disks a lot faster, making the process faster, then qtparted, but I also tend to do this with 5+ harddrives hooked to the computer at a time.  Either one you should be able to right-click the partition, and say format to <fs type here>.  Or if you're reinstalling Windows, just delete the partition and let Windows installer create a new one in the blank space.  The same is true if you've talked them into Ubuntu ;)

---

### Post by Rallg on 2009-03-28
You wish to wipe the ENTIRE hard drive, not just one partition? You wish to ensure that there are no hidden viruses, but are not trying to conceal information from an investigative agency? Then try this:

First, be sure that there are no writeable peripherals attached to your computer (such as a SD card in the slot).

Second, get a "live" Ubuntu, either on CD-ROM or USB. Boot to the live Ubuntu. Do not boot to anything on the hard drive.

Third, use the partition editor to determine the device corresponding to the hard drive. It may be /dev/sda or /dev/sdb depending on how you are using the live Ubuntu. I will suppose that it is /dev/sdX.

Fourth, ensure that no part of the hard drive is "mounted." If necessary, un-mount.

In Terminal:

sudo dd if=/dev/zero of=/dev/sdX bs=512

then go find something else to do, as it may take a long time to work. What it does is write 0 to all writeable parts of the hard drive, including the boot sector.

You will then need to format the drive. The above method should only be used if ordinary formatting (without writing 0 everywhere) doesn't work.

---

### Post by sgosnell on 2009-03-28
Or, you could just boot Windows as usual, open Start, Run, and type in "format C:".  That should format the HDD.  Booting from a live CD, deleting the partition, then putting on a new partition and formatting it would be more certain, though.  You can download a live CD with just gparted and the files necessary to boot [here](http://downloads.sourceforge.net/gparted/gparted-live-0.4.3-2.iso?use_mirror=voxel).  That might be the quickest method, if you don't already have a live CD ready.  Download the .iso, burn to a CD, and boot it, then do whatever you want to the HDD.

---

### Post by dcstar on 2009-03-28
> **mahela007 said:**
> I dunno about DBAN. However I am certain that what my friend (and I) wants is to format the disk. Does anyone know about a default partition editor on KUBUNTU?

As the others have stated, simply deleting the partition will do the job - just use whatever partition tool is on the distro CD you are using.

DOS/Windows "formatting" is nothing more than deleting a partition entry and doing a simple read on all the remaining data sectors to find any bad blocks.

The advice on wiping the drive is pointless (in your case) as it will do no more to give you a "formatted" drive than simply deleting the partitions.

---

### Post by mahela007 on 2009-03-30
thanks for the sugestions

---

