---
title: "Problems with reading/burning cd's"
date: 2006-01-16
forum: General Help
---

### Post by jerstew on 2006-01-16
I've been using Linux for about 10 years now. I have had the same CD Burner, a tdk-121032a for about 3 yrs now. I've used RedHat, Mandrake, Fedora, Slackware, Gentoo and a few others over the years and had very few problems with getting any of my hardware to work. Back in the days of ide-scsi emulation it worked fine, although maybe a little slower than normal. I switched to Ubuntu in October 05 after getting fed up with Federa, and I've been extremely pleased and impressed with it.

Here's a synopsis of my problem.
With the standard 2.6.12 Kernel that comes with Breezy, the burning process works great always at 12-13x, no coasters. When reading a cd (audio or data) to make a copy, the drive spins and reads very fast, probably closes to the 32x mark, but it always completely locks the machine. Can't switch to a VT to close anything, must cold reboot.

Secondly, if I recompile the Kernel and strip away unneeded drivers etc. The burner will read disks with no problem, fast too, but cd burning is slow - around 2-4x.

Also the problem is independent of software that I use, K3b, Gnomebaker, or command line tools. I've also tried three different burners, all have the same problem.

One more thing, when installing Ubuntu (5.10), It will lock my machine when coping additional packages at random points. (i.e. the burner drive is reading files/data quickly and therefore machine locks). This leads me to believe that the stock Ubuntu kernel has some option which locks my machine when reading cds. To install I started with the CD in expert mode, and loaded the ISO from my hard disk. So those of you who have had problems with the install locking during copying packages section might want to try that.

If someone could help me isolate the kernel option that locks the machine during the cd reading process, so I can remove it, and at the same time keeping the burning process up to speed, I would be very grateful.

Let me know if you would like to see my kernel config files or other information to help.
Heres my outdated hardware.
Soyo sy-5ema
AMD k6-2 550
512mb
TDK 121032A
WD 12G
Seagate 6G
Linksys NC100

Thanks for your help
jerstew

---

