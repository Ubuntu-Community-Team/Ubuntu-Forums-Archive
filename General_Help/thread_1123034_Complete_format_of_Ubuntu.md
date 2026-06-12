---
title: "Complete format of Ubuntu"
date: 2009-04-11
forum: General Help
---

### Post by uha8 on 2009-04-11
Hi, I got an Eee pc (netbook) which I have Ubuntu installed on. Now my mom is going to take over the computer, and she would like to start on a fresh system - still Ubuntu, but a clean one without all my crap. I'm not an Ubuntu freak (yet) so now i'm asking you: How do I completely format the machine using Ubuntu?

Ps: I thought about installing [GOs (link)]("http://www.thinkgos.com/gos/index.html") when the puter is formated, what do you guys think about that system? And do you know if it will be updated with the upcoming Ubuntu 9.04?

---

### Post by James_Lochhead on 2009-04-11
The easiest way to wipe the Hard Disk or SSD drive is to use live media. Since EEEs don't have an optical drive the easiest way to create would be to download Unetbootin and make an Ubuntu Live USB Flash Drive. You can use this Live USB Flash Drive to install Ubuntu and wipe the hard disk.

Personally, at this point I would just boot from the USB Flash Drive and start installing normally. When the partitioning screen pops up choose "Manual install". If you are using an SSD delete all the partitions (bye bye data), then create one partition formatted as ext2 and mounted at / (will be formatted by default). If you have an EEE with a hard disk read the normal installation instructions, they will be more beneficial to you than the SD method (only slightly harder).

In general terms the data is now gone. However, if there is something sensitive on there I recommend a shredding program; when you delete something on a storage medium it is not necessarily gone (this is how police catch criminals using their computers).

---

### Post by uha8 on 2009-04-12
Thank you! I didn't know that I could format from the installation. I have a portable dvd-drive, so I don't need Unetbootin (I used that in the beginning).
Can I format from the installation of any system, Such as GOs?

---

