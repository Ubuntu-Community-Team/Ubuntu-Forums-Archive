---
title: "Big hard drive, Old BIOS"
date: 2006-04-24
forum: Desktop Environments
---

### Post by AusIV4 on 2006-04-24
Hi,
Recently I've purchased a 250 GB WD Caviar hard drive. My system is about 7 years old, and the bios is not able to auto-detect the hard drive.

Western Digital provides some tools for tricking the bios into recognizing the hard drive, however the tools only work on Windows.

Can anyone point me towards tools for getting an older bios to recognize a large hard drive using linux?

---

### Post by jazzmuzik on 2006-04-24
Have you considered upgrading the computer's bios?

This is where you go to the motherboard manufacterer's website and see if there is a newer firmware available for your motherboard. If they have new bios software available, read and see if the update supports larger drives. If so, follow the instructions to install it. It then writes new code to the BIOS chip.

However, I have heard that Linux bypasses much of the information given in the BIOS. So you might still be able to install ubuntu and have it recognize the entire drive. I'm not totally sure about that though.

---

### Post by az on 2006-04-24
1.  Look up the motherboard's manual.  You can usually find them online.  You may find bios updates too.  Look at the changelogs of the bios updates to see what they fix.  Some state that they enable using hard drives greater than 80 gigs.

Often when the bios cannot handle a big drive, it means they can only see the first 80 Gigs.  It will work fine if you keep the bootloaded within those 80 gigs.  Linux, once booted, will see the whole drive.  

You can just make your system unbootable by filling up your drive and then installing the latest kernel.  It may get written to a part of the disk beyond the first 80 gigs and you will not get the bios to see it.

Ususally, you can play around with the jumpers and other devices on the ide cable to help get the new drive recognised.  In that case, the drive is not detected by the bios for other erasons than the size.  Can you enter the values of heads, cylinders and so forth by hand?

---

### Post by AusIV4 on 2006-04-25
The bios I'm using is not very well documented, and while I'm not using the most recent version of the BIOS, I've heard reports that the one version that is more recent is no better at mounting large drives.

As far as manually entering heads and cylinders, there is an option to do that. The documentation I have with the hard drive gives some values to enter, however even having tried this, the bios does not seem to recognize the presence of the drive. I get something to the extent of:

Primary Master: (Hard Disk 1 name)
Primary Slave: (Hard Disk 2 name)
Secondary Slave: (CD ROM name)

Secondary master drive fails

Press F1 to continue, DEL to enter setup

I've set the jumpers such that the hard disk I'm trying to mount should be the secondary slave, but it still tries to load as secondary master. I don't know if this is relevant.

I might mention, my current setup is temporary. In a few weeks I'll have a motherboard with a far more recent bios. The drive I ordered came from an eBay auction, and I want to test it and make sure it works within a reasonable timeframe, so that I might be able to resolve any issues as soon as possible. Even if I can't get the drive fully functioning on this system, can anyone recomend tools for testing a hard drive's reliability? (I assume this will at least involve getting the bios to recognize the drive).

---

### Post by jazzmuzik on 2006-04-25
There's nothing wrong with secondary master.

As Azz was saying, as long as you install the /boot partition within the first 80 gigs, you'll be fine. And to do that, during install, specify a separate /boot partition of 100 meg. (This assumes there are no Windows or other partitions on the disk) I find the linux installers like to put /boot first when it is a unique partition. Then once Linux starts up it will see the entire drive.

---

### Post by spade_shark on 2006-04-26
I agree with jazzmuzik on the setup.  Be sure to use the current kernels as well...hmm is this correct?
Large IDE disks (over 137 GB) use kernel 2.4.19.  All 2.6.X are fine.

---

### Post by methodical on 2007-12-30
I am having this same problem. Can someone tell me how to set up my partions manually?

---

### Post by gregcss on 2007-12-31
pre or post install?

---

### Post by methodical on 2007-12-31
> **gregcss said:**
> pre or post install?

Hey thanks I ended up figuring it out. I made a small /boot partition and it worked great.

---

