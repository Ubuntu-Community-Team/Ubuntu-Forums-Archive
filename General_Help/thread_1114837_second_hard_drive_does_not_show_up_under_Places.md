---
title: "second hard drive does not show up under Places"
date: 2009-04-03
forum: General Help
---

### Post by yosibeck on 2009-04-03
Using ubuntu Jaunty (but problem existed also in previous versions).
My Toshiba laptop has two 100GB hard disks.
I have installed Ubuntu (virtual installation - no real partition) on the first HD  with dual booting with Vista.
On the Ubuntu desktop I have an icon called "vista" which shows the Windows partition on the first HD, on which Ubuntu is installed.  
"Vista" is also shown as an option under Places from the Ubuntu menu.
However, the second HD (also Windows, called Data) is not shown on the desktop or under Places or in the Computer map in Places.
When I go to the media folder, "Data" is there alright, next to the "Vista" folder, and I can even access it perfectly, so I understand this second hard disk is mounted.
Why can't I get it to appear as an icon on the desktop and in the Places menu.
Any suggestions?
Yossi

---

### Post by kanikilu on 2009-04-03
I'm not sure why it's not there automatically, but, as a workaround, you could try bookmarking it in nautilus, which should add it to Places.

---

### Post by wineman on 2009-04-03
> However, the second HD (also Windows, called Data) is not shown on the desktop or under Places or in the Computer map in Places.

This is probably due to either the ubuntu kernel or nautilus finding fault with your disk, not specifically that you have a platter or read or any data-related error, it could simply just be that you have driver issues. 
i like what Kanikilu said, but as a precaution run checks in windows and ubuntu (fsck */dev/sdb1*, replacing sdb1 with your disk's device name). I wouldn't worry too much, just bookmark it, or add a link on the desktop.

Another thing you could try to eliminate the problem in the future is upgrade your nautilus version to the latest STABLE version from archive.ubuntu.com . My other fear is that nautilus could just be in beta, even though its unlikely

Hope this helps. Cheers

---

