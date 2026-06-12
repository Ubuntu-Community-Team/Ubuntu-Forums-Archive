---
title: "Faster boot by taking advantage of Linux's Filesystem"
date: 2009-01-18
forum: General Help
---

### Post by akimatsu123 on 2009-01-18
Hi,

I am relatively new to linux. I have been using Vista, which has a feature called Readyboost. It basically caches paging file/often accessed files onto a USB so the system can load it faster. People see it as "substitute for RAM"

Linux has more effective memory management, so "alternative RAM" isn't really necessary. But I was thinking, my computer has a SD slot that I always plug an SD card into (for Readyboost in Vista). What if i formatted this to ext3 filesystem, and put the often used files that are used at boot, and edited fstab to mount this as a folder? for example, basically run the folder "/usr" from the SD. 

Would this significantly improve performance/booting?? Just the speculations of a linux newbie...

---

### Post by itix on 2009-01-19
Well, it would be a pretty big procedure, but the new 4th extended file system (ext4) is pretty quick, so if you format the SD and put the booted files onto there and created symbolic links for them, you might improve the boot speed a bit.

It would require a bit of work though.

I also don't know where in the boot order the external disks are mounted, so something might go horribly wrong.

Say also that someone (a nephew or some smaller sibling) were to steal the SD-card, the system would become un-bootable.

Don't think that would be a good idea. Wait until jaunty comes out (it's about 3-4 months left) and things will hopefully go faster.

---

### Post by meindian523 on 2009-01-19
It would be easier to do the following:
1]When the screen shows Loading Grub 1.5,press Esc if the menu is hidden,otherwise press any key to stop the countdown.
2]Select the kernel line,and press e
3]In the prompt that opens,go to the end of the line and type ```
profile
```
4]Press enter,and at the Grub menu that appears,press b
5]This boot will be considerably slower than normal boots,but you should see a few seconds improvement in future boots.

---

