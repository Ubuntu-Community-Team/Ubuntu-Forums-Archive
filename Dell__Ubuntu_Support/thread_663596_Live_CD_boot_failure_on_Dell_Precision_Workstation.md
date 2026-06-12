---
title: "Live CD boot failure on Dell Precision Workstation 650"
date: 2008-01-10
forum: Dell  Ubuntu Support
---

### Post by kiplarsen on 2008-01-10
I am attempting to install Ubuntu 7.10 on a Dell Precision Workstation 650 which contains an Nvidia Quadro 4 980 XGL Graphics card.

BIOS Revision A04
MPTBIOS-IS-5.02.32

I am using a known good Live CD (have used the same CD to install on several other machines) and the CD drive is able to load any other application without problem.

I've tried "Safe Graphics Boot" mode and always get the same result.  

Last two lines on the screen at time of failure are:

Squashfs: version 3.2-Ubuntu (2007/07/26) Phillip Lougher
and
Kernal Panic - not syncing: Attempted to kill init!

nothing else happens, has anyone experienced this same problem? or have any ideas as to what might be happening here?

---

### Post by dirk_diggler on 2008-01-31
> **kiplarsen said:**
> I am attempting to install Ubuntu 7.10 on a Dell Precision Workstation 650 which contains an Nvidia Quadro 4 980 XGL Graphics card.

BIOS Revision A04
MPTBIOS-IS-5.02.32

I am using a known good Live CD (have used the same CD to install on several other machines) and the CD drive is able to load any other application without problem.

I've tried "Safe Graphics Boot" mode and always get the same result.  

Last two lines on the screen at time of failure are:

Squashfs: version 3.2-Ubuntu (2007/07/26) Phillip Lougher
and
Kernal Panic - not syncing: Attempted to kill init!

nothing else happens, has anyone experienced this same problem? or have any ideas as to what might be happening here?

I installed Ubuntu Gutsy using LiveCD on my precision 670, with NVIDIA Quadro FX 540.  It gave me serious errors as well.

My first problem was that my monitor would not work.  But, it was because I had a dual monitor setup.  I had to unplug one of the cables from the video card end, since turning off the power on one monitor did not do it.  Afterwards, this worked fine and I was able to proceed with installation.  Then, I upgraded my VC driver from NVIDIA, and everything worked fine, and set up with dual monitors.

I have "met" others who have had this problem also, but they had ATI xxx cards, which were known to have bugs with 7.04 (though you are using 7.10).

Have you tried using the text mode installer in alternate CD?  Also, how much memory do you have on your pc?

---

### Post by Mordac85 on 2008-04-16
I just ran into the same problem on my system.  I ran through the memory test and found 2 bad sticks.  Once I replaced those it ran like a champ.

Funny, but it was previously built as a Windows box and I didn't really have any indication of memory problems.  But since it was Windows how can you really tell?

---

