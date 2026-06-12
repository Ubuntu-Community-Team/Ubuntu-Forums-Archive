---
title: "Rescue scratched XBox 360 DVD?"
date: 2009-05-25
forum: General Help
---

### Post by ladasky on 2009-05-25
Yes, this is an Ubuntu question.
 
One of my son's Xbox 360 game DVD's has ceased to read, others continue to read fine.  I had a look at the disk, and I see a few minor sratches.  Not so serious to my eye, but the disk isn't reading.
 
Online resources say that DVD-RW drives can often read disks that DVD-R's cannot.  So I took the DVD upstairs and tried it in my Ubuntu machine.  It sees a video DVD, with a mere 5 megabytes in files.
 
I made an image file from /dev/dvd using ddrescue, and it is only 5 MB.
 
Some more reading leads me to guess that there's a second partition on this DVD.  The small one that I'm able to mount probably uses the standard UDFS file system.  Apparently the XBox has its own file system, which is what it will use in that second (much larger) partition.
 
Can I make a RAW image of the entire DVD, sector by sector?
 
Alternately, is there a tool (a FUSE plugin?) that would allow me to mount a partition in the XBox file system?
 
[This page]("http://forums.xbox-scene.com/index.php?showtopic=476989") gets me close to some resources that would probably help me, but the links are dead.
 
Thanks for your advice!

---

### Post by deadmnky on 2009-05-25
[http://www.llamma.com/xbox360/repair/xbox-360-repair.htm](http://www.llamma.com/xbox360/repair/xbox-360-repair.htm)
check that page out it may have some sources you can look at. or search the forums. sounds like the dvd drive is going out. send it back to microsoft the generally replace it for free. 
there was this thread as well 
[http://ubuntuforums.org/showthread.php?t=571961](http://ubuntuforums.org/showthread.php?t=571961) not sure if it works as i have never tried it good luck with it.

---

### Post by ladasky on 2009-05-25
Thanks, Dead Monkey...
 
I'll read through the XBox 360 repair page.  I had already found the page here on Ubuntu Forums to which you supplied a link.  The user in that thread already had an image file for the disk he was trying to copy.  I do not have that image file yet.

---

