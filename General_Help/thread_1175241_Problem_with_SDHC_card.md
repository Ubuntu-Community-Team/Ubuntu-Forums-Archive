---
title: "Problem with SDHC card"
date: 2009-05-31
forum: General Help
---

### Post by lotech on 2009-05-31
Hi there,

I've a strange problem reading memory card, my digital camera is using a 4G SDHC, but Jaunty has problem writing to it, no matter I put it in the card reader or via USB cable connection to the camera, the card become read only randomly, I have checked to make sure the write protect switch is not on but it is still read only some time, but it has no problem on windows, any idea ?

---

### Post by mb_webguy on 2009-06-01
I've had some problems with SD cards in the past which have universally been corrected by reformatting the card in Linux.  SD cards may not show up in gParted depending on the card reader you're using, but it's relatively painless to identify the associated device file using "df", then format the card using "mkdosfs /dev/*whatever*".  Of course, this will erase any files on the card, so make sure you back it up (using Windows if necessary) before you do this.

---

