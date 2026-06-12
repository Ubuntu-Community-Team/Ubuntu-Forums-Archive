---
title: "Adding CD as boot-option in BIOS (A07)"
date: 2007-08-06
forum: Dell  Ubuntu Support
---

### Post by OttifantSir on 2007-08-06
I have a Dell PowerEdge 500SC server
1GHZ
512 RAM
30GB HDD
Two LG CD-drives (one ROM, one RW)

I have, after a few mails back and forth with Dell Support and the good luck to find a floppy (thought I tossed them all away a few years ago), been able to upgrade the BIOS from A03 to A07 (floppy needed to install A05 which A07 needed to install).

But, the problem remains: I run XP Pro on it. I want to install Feisty Server on it, to make it a real server, not a desktop that is controlled via Remote Desktop. And there is no option in the BIOS to boot from CD.

Any ideas on how to enable this in BIOS?

I really want to install Feisty server, as this would be yet another step along the way to get rid of Windows.

---

### Post by pbcartwright on 2007-08-06
yer joking, right? a DELL server that can't boot from the CD??
While you were on the phone with Dell support, did you ask them??
I've never seen a poweredge that couldn't boot from CD, I install linux on poweredge servers all the time. Never seen a 500SC though...

---

### Post by dchriscoe on 2007-08-06
After pressing the F2 key to get to the bios screen, go to this option:

Boot Sequence Screen

The Boot Sequence screen options determine the order in which the system looks for the files that it needs to load during system startup. Available options include the diskette drive, CD drive, and hard drive. You can enable or disable a device by selecting it and pressing the spacebar. To change the order in which devices are searched, use the <+> and <-> keys.

---

### Post by OttifantSir on 2007-08-07
Starting with the first BIOS that was installed on it: A03. It had two options - Harddrive and Floppy. I managed somehow to enable PXE boot. So now, I have three options: Harddrive, floppy and PXE. Even after two subsequent BIOS-flashes. Through A05 because that's what A07 needed installed before it would do its own flashing.

I have looked over the entire BIOS for any hint on how to enable any of the two CD-drives (ROM and RW) to boot from. No luck.

I didn't pay much for this computer, only about $45-$50 used, so I don't lose a big investment if I fry the thing, but I bought it for a purpose which at the moment it is clumsily fullfilling, and which I believe a true server OS would make it fullfill perfectly: Be a server and free my laptop from being stuck to a desk because of my external drives.

So, anyone with intimate knowledge of LG CD-ROM CRD-8482B, LG CD-RW CED-8120B and BIOS A07 is much appreciated.

---

### Post by OttifantSir on 2007-08-10
Sorry for bumping this, but I really want to know if it is, at least, possible, and if possible, how do I do it?

---

### Post by mhilliard on 2007-09-06
PB,
we have been trying to get Ubuntu server installed on a Dell PE 2650 and some PE 2550's with Raid drives (PE 2650 had mirrored drives, and PE 2550's have RAID 5)

We can get basic OS installed but are having a lot of trouble accessing the HD array's.  We have heard online that this may be a problem with Ubuntu support or lack of support for the PERC 3 controllers.

Do you have any tips or strategies you have learned to get Ubuntu to work well with any of these Dell models?   Do you need to disable any of the builtin HW support to let Ubuntu work better??  If you have a few seconds to share your experience ti would be greatly appreciated!!!!

Mark H.
Mpls, MN USA

---

### Post by sr20ve on 2007-09-06
It sounds to me like it's not detecting the CDROM and if it doesn't detect the CDROM, it's not going to list that as an available option in the boot sequence.

I'm assuming it's an IDE CDROM. You might want to check the cable and jumper settings on the CDROM, or try swapping it out.

Does the BIOS list your CDROM on either one of the primary or secondary ports? If not, try turning each of the ports that might be turned "off" to "auto," see if it detects anything.

---

### Post by OttifantSir on 2007-09-09
As it has been running µTorrent on download for quite some time now, and will for some time to come, I haven't done much to check the availability in the BIOS the last couple of days, and having worked a bit so I haven't thought much about it.

Will do as you suggest at first possibility and post back what I find.

PS: I do believe they're IDEs, yes.

---

### Post by kwacka on 2007-11-06
I just came across this thread while searching for something else.

If you still have problems, try 'smart boot manager'

[http://linux.simple.be/tools/sbm](http://linux.simple.be/tools/sbm)

You can boot from cd even if not recognised by BIOS (I don't know how it would fare with old, proprietary drives, e.g. Dolphin).

---

