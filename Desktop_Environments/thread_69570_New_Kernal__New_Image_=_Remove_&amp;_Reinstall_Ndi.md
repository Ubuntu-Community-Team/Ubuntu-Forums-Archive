---
title: "New Kernal / New Image = Remove &amp; Reinstall Ndiswrapper?"
date: 2005-09-27
forum: Desktop Environments
---

### Post by zote on 2005-09-27
The last two times I installed updates to the kernal and the image, the updates were not complete without the routine of removing ndiswrapper, installing the kernal update and image and then reinstalling ndiswrapper.  I am using a HP Pavilion ZE4430 laptop with the infamous built-in Broadcom wireless card.  Using ndiswrapper with the bcmwl5.inf driver works well, but I wonder if there is a way to avoid having to uninstall and reinstall ndiswrapper each time I update the kernal.
I have been using the guidelines as posted in the Ubuntu Wiki, "SetupNdiswrapperHowTo" and will probably combine the terminal commands into a separate text to paste into the terminal to accelerate the reinstallation process.

Any comments or ideas welcomed
Thanks

---

### Post by KingBahamut on 2005-09-27
I believe that Ndiswrapper has a kernel module, so that any changes to the kernel, even the image, would require a reinstallation of ndiswrapper.

---

