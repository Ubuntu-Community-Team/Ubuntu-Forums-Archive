---
title: "changing the (dapper) LiveCD Bootsplash"
date: 2006-09-24
forum: Desktop Environments
---

### Post by jsgaarde on 2006-09-24
I have been trying to change the bootsplash of my LiveCD for some time now. It seems like there are two logos in use in the progress of booting. The first one is splashed in the selection face: livecd/isolinux/splash.pcx and it is easy to change. The next logo splashes after the boot selection, and here is the source of my problem. I have tried following:

First I thought that the squashfs file on the cd was mounted emmediately after the bootselection so that usplash was triggered. But after recompiling the usplash-artwork.so alternative to my own version and seeing absolutelu no effect I realized that it could not be squashfs's usplash. 

Then there is the livecd/isolinux/bootlogo file. What does that file do? and if it is here the livecd bootsplash is contained, how do I change it.

Anyway I think you get the problem: I can't change the bootsplash logo that appears after the boot selection. 

Best regards Jakob

---

