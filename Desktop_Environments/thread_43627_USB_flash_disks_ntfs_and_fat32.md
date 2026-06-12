---
title: "USB flash disks ntfs and fat32"
date: 2005-06-22
forum: Desktop Environments
---

### Post by IbeeX on 2005-06-22
Hello

I installed kbuntu and when I insert usb flash disk which is formated with fat32 it nicely appear on my desktop I mount it and works perfectly. But trouble is that I also haw USB external HD formated with ntfs and when I insert him it also appears on desktop butt it cant be mounted (no permission etc.) so I was looking at guides and forums and I updated my fstab and after that I can mount ntfs drive which is nice. But trouble is this that I now can't mount Flash disk (fat32) since that both use same dev/sda1 ??
What is solution for this I would like to be able to insert both devices (not in same time since I haw only one USB connector)
Any idea?

Ivan

---

### Post by intangible on 2005-06-22
What you need to do is write a udev rule for each so they always get assigned to a unique /dev/$name instead of just /dev/sda1 or whatever  (BTW, you would have a similar problem on Windows if you added and removed multiple usb drives, except for the not-reading NTFS part)

It's not exactly the most straight-forward thing to do, but these instructions should help:
[http://resolute.ucsd.edu/diwaker/articles/howtos/howto-usb-automount.html](http://resolute.ucsd.edu/diwaker/articles/howtos/howto-usb-automount.html)

I can help you hash out any details, just let me know if you need more help.

---

