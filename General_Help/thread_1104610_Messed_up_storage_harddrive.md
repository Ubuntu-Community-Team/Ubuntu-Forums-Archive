---
title: "Messed up storage harddrive"
date: 2009-03-23
forum: General Help
---

### Post by pEdRiDeR2008 on 2009-03-23
Ok, so I have 2 Harddrives in my desktop, 1x 120GB with Ubuntu 8.10 x64 and the other is a 250GB that had Vista on it, after not using the Vista for several weeks I decided to get rid of it and use the drive for storage.  So I formatted it with Gparted to ext3, removed the GRUB entry from menu.lst and then edited my fstab to mount the drive to /storage and then proceeded to load my music that I have on my server.  On my server (XP pro) I have 2 folders on 2 seperate hard drives each with ~80GBs of music that I was condensing to my one 250 in my desktop.

Well I let it run overnight because it takes a few hours and when I woke up, the transfer had "frozen" so I canceled it and tried again, but now the drive reads as having only 55GBs free even though I reformatted it with Gparted and restarted my computer.  Gparted sees it as a 250 with no usage, but nautilus says it is almost full.

Any ideas?

---

### Post by pEdRiDeR2008 on 2009-03-23
For some reason it fixed itself after I unmounted and remounted it several times.  Weird.

---

