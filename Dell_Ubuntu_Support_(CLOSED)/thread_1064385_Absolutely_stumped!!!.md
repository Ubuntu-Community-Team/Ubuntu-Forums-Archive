---
title: "Absolutely stumped!!!"
date: 2009-02-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nfs on 2009-02-08
I have a Dell Dimension 2400 collecting dust in the corner with an old Debian distro and XP as a dual boot, and a CPU intensive application that I really can't run on my usual machine without causing problems, so thought I would install a new copy of ubuntu on it.

Downloaded the 8.10 LiveCD ISO.  Burned it onto a CD.  The image verifies.  Plunked it into the Dell, flipped the switch, hit F12, chose boot from CD.  Got a plausible looking menu.

Now comes the problem.  No matter what option I choose - try us out, install, check memory, anything - the CD spins for a few seconds, the video goes nuts, and everything hangs.

I've looked for similar reports on the forum.  I've tried raising and reducing video memory: no go.  I've tried booting in safe graphics mode: no go.

Machine specs:

Dell Dimension 2400
Pentium P4 2.2GHz
384Mb memory (I know this is low)
64Mb video memory
Onboard Intel graphics chipset

Anybody got an idea?

---

### Post by utnubuuser on 2009-02-08
This is probably not the correct way to go abut this, but have you tried installing "server version" then adding the desktop environment?  Or maybe the alternate install CD since the available memory is marginal?

---

### Post by ahood on 2009-02-08
May want to try the alternate installation iso and install with a command that disables apci (acpi=off I believe). I will need to do a bit of searching to find the absolute right command. No time now, but will later if not already posted.

DrH

---

### Post by armandh on 2009-02-09
was this box flakey when kicked to the corner
how much dust is inside in the heat sinks?

first try the disk to run live on a known good working computer
OK > disk probably good
try a known good working CD drive 
Still no live Ubuntu > try memory test/and if good more memory, 
or adjust on board video's use of memory to minimum as
probably too much used for on board video.

dont forget the usual inspection for loose cables, boards. etc.

---

### Post by billyboy1995 on 2009-06-20
i have not done any changes to my 2400 and i can get 9.04 to work perfectly...so my two suggestions are... 1) vacuum all of the dust and 2) try 9.04

---

### Post by mattwilkes512 on 2009-06-24
> **billyboy1995 said:**
> i have not done any changes to my 2400 and i can get 9.04 to work perfectly...so my two suggestions are... 1) vacuum all of the dust and 2) try 9.04

Do you have a PCI sound and/or graphics card in your dimension 2400.  I dont and upon fresh install of 9.04 compiz is disabled (low graphics) and sound does not work.  How did you fix this?  Thanks.

---

### Post by billyboy1995 on 2009-07-08
i didn't have to do anything to mine to make it work. have you checked your master controls? or try a new pair of speakers.

---

### Post by billyboy1995 on 2009-07-08
sorry i forgot to say no i don't have any pci cards in mine.

---

