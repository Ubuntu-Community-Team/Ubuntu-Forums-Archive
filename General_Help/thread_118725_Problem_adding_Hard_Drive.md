---
title: "Problem adding Hard Drive"
date: 2006-01-17
forum: General Help
---

### Post by kenquad on 2006-01-17
Hi all:

I'm trying to add a 6.4 GB slave drive to my Kubunu Breezy box.  It's correctly recognized by the BIOS but Kubuntu doesn't see it.  I added an entry in /etc/fstab but got only error messages for my trouble.

Help!

Thanks,
kenquad

---

### Post by earobinson on 2006-01-17
can you post your /etc/fstab and the error msg?

---

### Post by kenquad on 2006-01-17
Okay, I just (DUH!) discovered the Kcontrol applet for changing filesystems and got it working until I changed the disk to NTFS.  Maybe a restart will work.  Anyway, I'm out of time now and will post again with results.  Thanks.

---

### Post by kenquad on 2006-01-18
Hi again:

Well I sort of had my HD recognized for a minute there....  Okay, please bear with me while I unveil what is probably a laughable chain of stupidities.  Today when I logged on my HD was not recognized by Kubuntu - that is, I could see it but it wouldn't mount.  

To make a long story short, I checked the error messages and found that the "quiet" command was fouling things up.  Guessing that this corresponded to "Suppress permission errors" in Kcontrol, I disabled that option.  BINGO!  The HD mounted and the errors dissolved.  Then it gave me an error that it couldn't access the mount point, which I had selected as /media/hdb.  Not bingo.  So I changed the mount point to /dev/hdb - but there was already a file called /dev/hdb so I temporarily renamed that /dev/hdq and created a folder to mount my drive.  Oddly, while I still couldn't access it from Storage Media (same can't access error), I was able to browse its contents by navigating to /dev/hdb! 

I restarted, hoping this would iron out the errors.  It didn't.  In fact, it got rid of my /dev/hdb directory entirely and renamed /dev/hdq back to /dev/hdb!!!  I think the whole problem must stem from a mount point issue.  Please help.

Thanks,
Kenquad:confused:

---

