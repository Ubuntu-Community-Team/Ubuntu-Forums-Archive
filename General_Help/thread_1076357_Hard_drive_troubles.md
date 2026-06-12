---
title: "Hard drive troubles"
date: 2009-02-21
forum: General Help
---

### Post by costre on 2009-02-21
I have a software raid array which contains 4 TB of data.

I want to try to create a hardware raid array, but I need to backup all the data before I start.

I have one 2TB external USB-harddrive, one 1TB external USB-harddrive, and one 1TB internal sata drive.

I have copied 3 TB in total to the two external drives, but I am having trouble copying the last TB to the internal drive. It could be that the drive it's starting to fall apart, but I wanted some input before I go buy yet another 1TB-drive.

About 80 GB into the copying process I get this message:

```
There was an error copying the file into /media/disk.
Error writing to file: Read-only file system
```

I have also noticed that I can't find the particular drive (/dev/sdl) in Gparted until I reboot.

I am not freaking out, since no data has been lost, I'm just wondering if there's a mundane explanation for this.

---

### Post by costre on 2009-02-21
Just a quick update.

I tried partitioning the 1TB-disk into one 900 GB filesystem, starting 100 GB in from the start of the drive, hoping to avoid the region of the disk reached when ~80 GB has been written.

It seems to be working, I have copied 250 GB so far without problems. Bummer, seems like a physical error on the drive :(

Perhaps I can get a new one using the warranty, the computer is not even a year old. 

(BTW, I borrowed a 300 GB external drive to take care of the 100 GB of data, that I lost room for when I re-partitioned the big drive.)



Of course, if anyone has ideas of disk-analysis, diagnostics or possible repair options, feel free to post your suggestions.

---

### Post by handy on 2009-02-21
You may find a test or other useful information for your drive at the following page:

*_[http://www.ariolic.com/activesmart/low-level-format.html](http://www.ariolic.com/activesmart/low-level-format.html)_*

---

