---
title: "Unknown filesystem in Thunar"
date: 2011-05-10
forum: Desktop Environments
---

### Post by urukrama on 2011-05-10
I've upgraded to Xfce 4.8, and now have an additional hard drive in my Thunar side pane--a hard disk that as far as I know does not exist! :confused:

A 6.4 GB filesystem shows up in the side panel (see the first attachment), even though I don't have a 6.4 GB internal hard drive or partition (I do have a 5.9 GB partition for / ) and no external hard drive is currently attached to my computer. 

If I try to (un)mount or eject it by clicking on the drive icon or the eject button, I always get an error message the filesystem failed to mount because a "Daemon is inhibited" (see second attachment).

That filesystem never showed up in the old Thunar (that came with Xfce 4.6).

Any suggestions?

---

### Post by ManualSparrow on 2011-05-10
I had a similar problem when I formatted an external hard drive - check and see if it shows up in Gparted or whatever Disk Utility you are using, to make sure it actually doesn't exist.

---

### Post by urukrama on 2011-05-11
> **ManualSparrow said:**
> check and see if it shows up in Gparted or whatever Disk Utility you are using, to make sure it actually doesn't exist.

I checked that before I posted. I don't have a partition that size, and all the partitions I do have are used and accounted for.

---

### Post by urukrama on 2011-05-14
Thinking that perhaps there might have been some conflict with configuration files of older Thunar versions, I removed all those. I still get the error message, but now it says "Authentication is required." (instead of "Daemon is inhibited")

So I tried to run Thunar as root to figure out what the filesystem is, and noticed the filesystem does not show up when I run as Thunar as root.

---

### Post by ManualSparrow on 2011-05-14
Have you tried looking for it in the disk utility and/or a different file manager? (PCMan FM is faster than Thunar surprisingly, so you could easily justify checking it out).

---

### Post by urukrama on 2011-05-15
I did. No other file manager shows it, neither does GParted, nor does Thunar when run as root.

---

