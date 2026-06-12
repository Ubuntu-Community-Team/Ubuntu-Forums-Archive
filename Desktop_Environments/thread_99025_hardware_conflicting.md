---
title: "hardware conflicting??"
date: 2005-12-04
forum: Desktop Environments
---

### Post by kpm on 2005-12-04
Hi,
I have an old P3 that uses a wireless infrared keyboard that also acts as a mouse via controls on the keyboard (PS2).  It works fine.  I also pluged in a usb mouse (since the one on the keyboard are not the most efficient) and it worked fine.  Then I plugged in my portable USB hard drive with NTFS file system and it worked fine... this is quite exciting to me since the last time I installed Linux (almost 8 or 9 years ago, getting everything to talk was torture). 

But, then the USB mouse stopped working, if I reboot it would work for moments then stop or sometimes work for a long while then quit... If I boot up without the portable hard drive connected, then the USB mouse would work flawless... So, the two USB components are fighting over resources... If I were using Windows, I would check the Device Manager to see if there were any resource conflicts, what do I do in Ubuntu Linux to correct this issue?

Thanks for any help

---

### Post by Ocxic on 2005-12-04
i would agree with you assesment that the mouse and HD are fighting over resources, tho it may just be your external HD using too much of the badwidth. if you can try pluging in the mouse or HD in a different USB port on your computer. hopefully that way it'll use a seperat USB bus controller, and you won't have the problem.

---

### Post by kpm on 2005-12-04
Well that is interesting, I never realized one usb port would out do another... but it seems to work now... Since this old machine only has two usb ports, I just flipped them around... and voila, I am using my mouse to browse my music on the portable USB hard drive (which is USB 2.0 compliant, though the ports are not...).  I sure did notice that the original reading of the music directory with Nautilus was much slower than when it was plugged into the other port... but that is not much of a problem considering I now have a mouse... hopefully it will all keep working fine and I will put a note on the back of the PC warning users to always plug USB hard drive in the one, and mouse in the other.
Thanks!

---

