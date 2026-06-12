---
title: "Ubuntu detects DVD/RW but Windows does not."
date: 2009-02-10
forum: General Help
---

### Post by SlayerOfLight on 2009-02-10
Like the title says, Ubuntu detects my DVD drive but windows does not.  Does anyone have any idea what might be causing this?  Windows stopped detecting my DVD Drive shortly after I installed Ubuntu.

If it makes a difference I have a Windows Partition, a NTFS partition (drive for both OS to share), Ubuntu partition, small swap partition.

---

### Post by cariboo on 2009-02-10
This is a pretty common problem, I've seen it many times in XP too. Boot into Vista nad try this:

```
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Class\{4D36E965-E325-11*CE-BFC1-08002BE10318}

Apparently it seems that this is an age old fix for even XP systems. If you venture to the registry key above by doing the following steps:

   1. Click on the start menu.
   2. If this is a Vista machine in the search box type in “regedit” without the quotation marks.
   3. Maximize the HKLM and then go ahead and browse until you reach the key listed above.
   4. In the right panel you’ll see something along the lines of “UpperFilter” and “LowerFilter” you want to click on each “filter” key and hit delete. Click yes when it asks to confirm if you wish to delete the key.
   5. Restart Windows.
```

Jim

---

### Post by SlayerOfLight on 2009-02-11
Hi,

That was one of the first things I tried.  I even deleted them in each of the different control sets and it still did not detect it.  I wiped my drive and did a fresh install and the DVD drive was then detected, however this morning I did Windows update and it disappeared again.

Sounds like a windows issue, thanks for your help though.  If you have any other suggestions I'd be more than happy to hear them.

---

### Post by SlayerOfLight on 2009-02-12
After some extensive research, much deeper than I had done before.b

Apparently Grub doesn't play well with some Optical Drives on IDE when the Disk drive is Sata or RAID.  This in turn makes it so the Windows, or even both operating systems, can't access or even detect the CD Drive.  

I fixed this by, unfortunately completely wiping my drive (for like 5th time this weekend).  Installing XP on one primary partition, Installing Ubuntu  on a different primary partition using the advanced options and not installing a boot loader. I then booted from the Live CD and install Lilo for Ubuntu running off the LiveCD (since for some reason it did not install any of the splash images to the boot directory when it first installed Ubuntu).  After doing that I copied the splash images from the temporary directory to the root drive's Boot directory.  The following link helped me configure Lilo and sort helped me figure out how and where to copy the images.

[http://users.bigpond.net.au/hermanzone/p4.html](http://users.bigpond.net.au/hermanzone/p4.html)

Anyway, I'm quite impressed with myself since I've never used Linux before this weekend (I'm somewhat familiar with Unix though).

---

### Post by mc4man on 2009-02-12
If you happen back it would be interesting to know what dvd drive you have, I've seen this once with a samsung

---

### Post by SlayerOfLight on 2009-02-12
> **mc4man said:**
> If you happen back it would be interesting to know what dvd drive you have, I've seen this once with a samsung

Pioneer dvd-rw 16-dvr

---

### Post by 1ronlung on 2009-02-12
You might want to edit the thread title to include '[solved]'.  Never come across your problem personally, but I'm sure someone out there will find your solution invaluable :)

---

