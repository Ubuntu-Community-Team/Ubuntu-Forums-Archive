---
title: "USB memory"
date: 2008-07-16
forum: Desktop Environments
---

### Post by Zoom78 on 2008-07-16
Hi!

I've just installed Kubuntu and I'm wondering how to access data from a USB memory. I've plugged it in but I cant seem to access it?

---

### Post by ProbablyX on 2008-07-16
Try clicking the icon in your lower right that looks like a computer. It should open up a list with plugged-in harddrives and memories.

---

### Post by Zoom78 on 2008-07-16
> **ProbablyX said:**
> Try clicking the icon in your lower right that looks like a computer. It should open up a list with plugged-in harddrives and memories.

OH! Thanks, I'm so stupid...

---

### Post by peakshysteria on 2008-07-16
```
lsusb
```will tell you if Kubuntu detects it at all. If not it might just be that you haven't removed it properly from a windows machine (safe removing of hardware). Just mount it in windows and unmount it the proper way and it should pop up in Kubuntu.

Or take a look at:[How to Mount USB Disk Drive in UNIX or Linux]("http://www.mydigitallife.info/2006/09/10/how-to-mount-usb-disk-drive-in-unix-or-linux/")

Or can it be:
[https://bugs.launchpad.net/ubuntu/+bug/225931](https://bugs.launchpad.net/ubuntu/+bug/225931)

---

