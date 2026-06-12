---
title: "NTFS HDD problem."
date: 2009-01-30
forum: General Help
---

### Post by Slingshot124 on 2009-01-30
Alright, I recently bought a dell computer and it came with Ubuntu. So, I went out and bought Windows Vista and attempted to install Windows over Ubuntu, but, it kept telling me I need a HDD with at least 15 GB of available space, and it has to be NTFS. And, none of the HDDs are NTFS. My question is, how do I make my HDD NTFS so that I can install Windows Vista onto it?

---

### Post by Neural oD on 2009-01-30
the vista disk should allow you to format the disk 
But question - why are u going backwards?? - no offence intended; but my laptop came with vista - which i took off to put ubuntu on - couldn't be more happier - more stable, secure, and zippier

---

### Post by taurus on 2009-01-30
You need to download a GParted LiveCD, [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php), and boot from it.  Then, use gparted and delete all the partitions on your harddrive.  Then, create a new one that takes up the whole harddrive and format it to ntfs filesystem.  Now, windows should be able to read the harddrive this time.

---

### Post by Slingshot124 on 2009-01-30
> **taurus said:**
> You need to download a GParted LiveCD, [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php), and boot from it.  Then, use gparted and delete all the partitions on your harddrive.  Then, create a new one that takes up the whole harddrive and format it to ntfs filesystem.  Now, windows should be able to read the harddrive this time.

I wrote gparted onto a CD and booted from it but I can't figure out how to delete all the partitions using it. And the FAQ on the gparted website doesn't say anything about it.

---

