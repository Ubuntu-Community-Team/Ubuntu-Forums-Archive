---
title: "[kernel bug?] Problems with external USB disk"
date: 2006-05-18
forum: Desktop Environments
---

### Post by 123dfdfg43 on 2006-05-18
Hi everybody.

I have an annoying problem with an external USB drive (a **Lacie 160GB USB 2.0**, formatted in **fat32**), with kernel **2.6.12-9-k7**.

The following actions works fine:
- plugging in / mounting
- copying any files from PC to disk;
- copying very small files from disk to PC;

Otherwise, this action hangs and aborts, and I have to unplug the disk and remount it:
- **copying a big file from usb disk to PC**.

Under Windows XP the disk works fine.
I think this is a kernel problem, probably related to buffering/caching of big files.
The problem is totally reproducible, it happens EVERY time. After the problem, the fat32 is often corrupted and I have to fix it under Windows.

What can I do? This is very annoying, as you can imagine... ](*,) 
I have read this page, but I haven't found any clues:

[http://www.linux-usb.org/usb2.html](http://www.linux-usb.org/usb2.html)

Thank you in advance,
Andrea

---

