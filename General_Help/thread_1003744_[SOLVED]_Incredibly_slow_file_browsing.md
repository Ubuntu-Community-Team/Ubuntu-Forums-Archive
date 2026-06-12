---
title: "[SOLVED] Incredibly slow file browsing"
date: 2008-12-06
forum: General Help
---

### Post by AdmBeatty on 2008-12-06
Hi, I'm hoping someone can tell me why my file browsing is so incredibly slow!  I am running:

Intrepid Ibex 8.10
Intel Core2 Quad 2.83 Ghz
8Gb RAM
1Tb SATA II Hard Disk

Whenever I try a function which requires file browsing, it takes forever to load.  This can be 30 seconds to simply open Nautilus to my home folder, or to enter my music folder (which admittedly has about 100Gb of files), it essentially hangs (I haven't tried waiting for it more than 20 minutes...).  I should add that this is a new phenomenon, and that it has been running fine until the last few days.  The system monitor shows I am using about 25% of my available processing power, and 20% of my memory; indexing is allowed.

Any ideas?

---

### Post by unutbu on 2008-12-06
If you have a lot of files in one directory, you might see a performance boost by putting files into subdirectories.

Perhaps also try going to nautilus Edit>Preferences. Click on the Preview tab and see if turning off all previewing helps.

---

### Post by AdmBeatty on 2008-12-06
My music is divided into subdirectories, though I'll grant there are a lot of them.  However, I'm concerned that it takes 30 seconds to open to the 20-odd files/folders in my Home directory.  I have tried disabling icon preview with no joy...

---

### Post by unutbu on 2008-12-06
Hm, my knowledge of nautilus has been exhausted :(

To make sure the problem is truly localized to nautilus, let's check that command line is okay:

Please open a terminal and type
```

time ls -la
```
How long does it take?

---

### Post by AdmBeatty on 2008-12-06
milliseconds :-(

---

### Post by unutbu on 2008-12-06
Well, at least the problem isn't system-wide.

What has changed about your system recently? For example, did you start mounting a samba share? 

Googling "nautilus slow" came up with this:
[http://ubuntuforums.org/showthread.php?t=470947](http://ubuntuforums.org/showthread.php?t=470947)

If your problem is the same as buckwheat12n's, then the slow-down should only occur when in List View. Is that the case?

---

### Post by AdmBeatty on 2008-12-06
Hmm, I recently installed Amarok, and un-installing it seems to have sped everything up again.  problem solved, though I don't see why this should have made a difference even when Amarok wasn't running...  Many thanks for the help : - )

---

