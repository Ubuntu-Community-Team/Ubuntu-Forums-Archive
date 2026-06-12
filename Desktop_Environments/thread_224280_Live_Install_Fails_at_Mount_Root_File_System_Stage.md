---
title: "Live Install Fails at Mount Root File System Stage"
date: 2006-07-27
forum: Desktop Environments
---

### Post by craigfoster on 2006-07-27
Read some of the other posts but haven't found a satisfactory answer yet.

Insert Live CD (6.06 ISO downloaded and checksum is OK) and get to boot screen.

Tried booting the live CD but only get as far as the 2nd step "Mounting root filesystem" and installer hangs. Also hangs if try to check the CD for errors.

Other forum postings mention booting in "verbose mode" to debug any errors but haven't found any instructions on how to do this.

Other posts mention a Hard Drive or CD/DVD drive issue or an issue with SATA and Enhanced Mode. Any ideas?

PC built by me 2 years ago and I remember having trouble getting the CD/DVD Drive and HDD to set up correctly. I've never been totally happy that this was correct and on booting I always get a S-ATA Promise Driver - BIOS not installed error. But WinXP boots and has been fine for 2 years so why fix it...

If it helps BIOS Settings for "On Chip IDE Config" are:
On-Chip ATA(s) Operate Mode: Legacy
ATA Configuration: S-ATA Only
S-ATA Keep Enabled: No
P-ATA Keep Enabled: Yes
P-ATA Channel Selection: Primary
Combined Mode Option: S-ATA 1st Channel
S-ATA Ports Definition: P0-1st / P1/2nd
Configure SATA as RAID: No

DVD/CD ROM reports as HL-DT-SW RW/DVD GCC-4120B

---

### Post by silex on 2006-07-27
I had gotten the same root filesystem and cd check errors while installing Ubuntu on a laptop the other day.  I just burned a new copy of the install CD and the new copy worked fine, though that probably isn't the most helpful advice.

---

### Post by craigfoster on 2006-07-28
CD was fine as ran the live version on a Dell Laptop.

Have investigated a bit further on these forums and it looks like I'm just one of many who are having the same problem:
[http://ubuntuforums.org/showthread.php?t=186115]("http://ubuntuforums.org/showthread.php?t=186115")

Should have posted this thread under the one above. Unfortunately it would just be to add to a long list of "me too" postings.

Bit of a newbie to Linux but did have tinker with Mandrake a few years back but moved back to XP when built the new PC. Heard lots of good things about Ubuntu and thought I'd give it a whirl. Needless to say I'm a bit dissappointed.

---

### Post by silex on 2006-07-29
Have you tried the Alternate install CD?  It is an install only CD that has a bunch of extra options for tricky things like OEM installation and low memory computers, so it might take a little more care in choosing install options, but it might not have the problem the live CD does.

---

