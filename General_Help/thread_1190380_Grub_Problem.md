---
title: "Grub Problem"
date: 2009-06-17
forum: General Help
---

### Post by ghandi69_ on 2009-06-17
First off, I apologize for starting a new thread, I was able to find a few threads regarding my issues but I wasn't sure it was quite the same situation.

I had a setup with 2 hard drives, sda and sdb, both sata drives.  Sdb had ubuntu loaded on it, and sda was a backup disk.

I recently formatted the first hard disc, sda with windows xp using the xp pro install disc.

After getting that setup to run correctly, I wanted to boot back into my Ubuntu machine.

During bootup, I press f12 to select the ubuntu disc.  When it tries to startup, I get an error that reads "Error Loading OS"

I think I have to get a liveCD and then make some changes from what I've read, but I'm not sure.  I havent lost everything on my sdb drive have I?

---

### Post by maheshasolkar on 2009-06-17
Looks like a messed up grub:

  [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

From all the alternatives suggested there (pretty overwhelming list, really!), I usually use the SuperGrubDisk:

  [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

