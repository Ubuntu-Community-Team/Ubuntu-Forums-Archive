---
title: "Uninstall help!"
date: 2009-02-04
forum: General Help
---

### Post by bearnet2001 on 2009-02-04
Hi,

Just got a brand new comp and installed ubuntu. Am not really interested in it for a number of reasons (thought I would be). 

My question: How do I uninstall ubuntu so that I can install Win XP from a boot CD afterwards? I want my HD to be where it was when it was brand new and ubuntu wasn't installed, ie I want ubuntu completely removed.

Thx!

---

### Post by finer recliner on 2009-02-04
just toss the Windows XP install disc in your computer. boot from it. The windows installer will eventually scan your hard drive for existing partitions and ask where you want to install Windows. From here you can choose to delete your existing partitions (like ubuntu). You can now format the newly freed space and tell windows to be installed there.

Warning: you will lose all of your all of your files and data from the partitions you delete (or accidentally overwrite). Backup anything important to a USB thumb drive first.

---

### Post by bearnet2001 on 2009-02-04
> **finer recliner said:**
> just toss the Windows XP install disc in your computer. boot from it. The windows installer will eventually scan your hard drive for existing partitions and ask where you want to install Windows. From here you can choose to delete your existing partitions (like ubuntu). You can now format the newly freed space and tell windows to be installed there.

Warning: you will lose all of your all of your files and data from the partitions you delete (or accidentally overwrite). Backup anything important to a USB thumb drive first.

So I can format from within the XP (Or say Windows 7 beta, might try that) boot disk and that will completely clear out anything I've had on my HD previously?

---

### Post by howefield on 2009-02-04
> **bearnet2001 said:**
> My question: How do I uninstall ubuntu so that I can install Win XP from a boot CD afterwards? I want my HD to be where it was when it was brand new and ubuntu wasn't installed, ie I want ubuntu completely removed.

If it came loaded with Win XP, you may have a recovery partition or recovery media which will take you back to when you bought it.

---

### Post by bearnet2001 on 2009-02-04
> **howefield said:**
> If it came loaded with Win XP, you may have a recovery partition or recovery media which will take you back to when you bought it.

It came with no OS

---

### Post by RedSingularity on 2009-02-04
Then yea.....boot whichever version of windows you like.  It will give you an option to reformat which will completely erase Linux.

---

### Post by bearnet2001 on 2009-02-04
> **Shadow121 said:**
> Then yea.....boot whichever version of windows you like.  It will give you an option to reformat which will completely erase Linux.

how do i make it so it boots to the XP cd rather than into ubuntu at start?

---

### Post by RedSingularity on 2009-02-04
Put the CD in and reboot.  Do you have BIOS set to boot from CD before HDD?

---

### Post by bearnet2001 on 2009-02-04
> **Shadow121 said:**
> Put the CD in and reboot.  Do you have BIOS set to boot from CD before HDD?

No. How do I do that?

---

### Post by RedSingularity on 2009-02-04
Once you reboot Hold F9.  Then just select your DC drive.

---

### Post by bearnet2001 on 2009-02-04
Need help!

I got the Win XP CD to run, and its trying to install but its asking me about partitions. 

I have C: and E: partions. C: is 930gigs (all free), E: is 23 gigs, all free. I have a 1 tb WD drive with ubuntu installed... I really don't want to break my computer (though I want to get completely rid of ubuntu)!

I have options to delete the partitions or install on them. However when I go to install on the C: partition it says windows cannot recog. the partiion, tells me to delete it. But if I do so will that break my HD or my mobo bios? It says that C: partition has system files (is a "system partition") that may be important. I know WD 1tb drives are supposed to have 930 gigs capacity... 

What do I do?

---

### Post by RedSingularity on 2009-02-04
Oh its fine.  You can delete them.  Nothing will break.  Just delete them and then re-partition them with the CD.

EDIT:  Windows cannot recognize it because Ubuntu formatted with the ext3 format.  Windows uses NTFS format.

---

### Post by RedSingularity on 2009-02-04
For future reference, you can do whatever you want with the HDD.  There is no essential information to the BIOS on it.

---

### Post by howefield on 2009-02-04
Sorry, misread something..

---

