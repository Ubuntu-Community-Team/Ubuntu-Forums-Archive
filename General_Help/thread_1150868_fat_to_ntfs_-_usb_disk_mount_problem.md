---
title: "fat to ntfs - usb disk mount problem"
date: 2009-05-06
forum: General Help
---

### Post by enaros on 2009-05-06
Hi guys,

I have a little problem. I've converted my 320gb usb disk from fat32 to ntfs using this guide: [http://support.microsoft.com/kb/307881/](http://support.microsoft.com/kb/307881/)

Basically I had to run the following command in windows:

convert drive letter: /fs:ntfs

I did that because my disk already had information and I wanted to change the filesystem without having to backup (or lose) all my files.

Well, the problem here is that my new shiny ubuntu (9.04) can't detect the disk. Indeed, it detects the disk, but does not detect the disk filesystem (ntfs now).

Is there a way to fix this? or...
Am I screwed? (and what I need is to re-format my disk from the beginning)

Thaks for your help

---

### Post by HermanAB on 2009-05-06
Howdy,

Install ntfs3g, the NTFS file system for Linux.

---

### Post by enaros on 2009-05-06
Thanks Herman,

But I think ubuntu 9.04 has ntfs3g pre-installed, hasn't it?
I mean... It reads my 2Gb ntfs pen drive but not my fat32-to-ntfs-converted usb disk

Can u help me please?

:)

---

### Post by Legace on 2009-05-06
Try to mount your disk on Windows, then safely remove that disk, and try to remount on Ubuntu.

---

### Post by Spiritous on 2009-05-06
320gb usb disk

My god! I didn't know they were that big :S

---

### Post by Legace on 2009-05-06
> **Spiritous said:**
> My god! I didn't know they were that big :S

Probably something like Western Digital My Passport :)
[http://www.wdc.com/en/products/Products.asp?DriveID=391](http://www.wdc.com/en/products/Products.asp?DriveID=391)

(not a true flash USB disk, but one with a integrated harddisk)

---

### Post by enaros on 2009-05-06
Thanks for your reply Legace, but that is not the problem, I already did it.

I think the problem relies on the convertion (from fat to ntfs) I made on the disk.

Using GParted, I can see the usb disk (under /dev/sdb), it detects the disk size, but not the filesystem... Furthermore, GParted says that the partition is unallocated, but It works perfectly fin in windows xp.

@Spiritous: I have a Samsung usb disk :) It's really cheap and works great, It's very fast indeed.

Anyone can suggest something different ?

---

### Post by enaros on 2009-05-08
Any idea???

Please, don't let this post die!

Help me :)

---

