---
title: "Recovering data from hard drive (or fixing the system)"
date: 2006-09-20
forum: Desktop Environments
---

### Post by mssever on 2006-09-20
My brother has a ~2-year-old Dell laptop running Windows XP Home. He had left it on for several days by accident (at which point it was running fine), and when he came back to it, it was non-responsive. He hit the power button to reboot it and on boot, Windows complained about not being able to find ntoskrnl.exe (which is XP's kernel, I believe). Of course, Windows won't boot. The BIOS gave some errors when he ran a test in setup. I don't remember what they were, however.

He booted from the Dapper live CD to try to rescue his essential data and called me. I had him run fdisk, and fdisk didn't find any partitions on hda. I know for a fact that there are at least three partitions on that disk. fdisk also complained about a mising disklabel. (Incidentally, he told me that when the live CD booted, he saw several errors related to hdc--which is the CD, I believe.)

I suggested that he try to pull the hard drive out of his laptop and put it in his wife's (very similar) laptop. Unfortunately, the hard drive proved too difficult to remove.

My theory is that somehow the partition table got hosed, although the BIOS and Ubuntu's hdc errors don't seem to fit with this theory.

Here are my questions:[LIST]
[*]Does anyone have any better ideas about what might be wrong, or additional troubleshooting steps to take?
[*]Does anybody know how to recover data from the drive; or, can anybody recommend a data recovery service in the US (preferably in Nebraska) that is reasonably priced?[/LIST]

---

### Post by lagagnon on 2006-09-20
Sounds to me like a hard drive problem, but I might be wrong. Find out the hard drive manufacturer and download their bootable diagnostic diskette (from their website). That will tell you if it is a HD problem.

---

