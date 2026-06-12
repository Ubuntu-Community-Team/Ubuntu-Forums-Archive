---
title: "Dell D600 hibernation problem"
date: 2009-07-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by GavinWiggins on 2009-07-01
Hello,

My problem is this:

When I try to hibernate my computer, it tries to hibernate, but then comes right back to the password unlock prompt.  This started happening after a friend did some partition editing.  I've read some threads in search of an answer, and my swap space seems to be plenty big enough.  Any ideas?  Thanks.

---

### Post by coffeeaddict22 on 2009-07-01
Hi,
Lots of ideas; dunno which is of most use!
Try doing a hibernate, then on restarting open a terminal and type in ```
dmesg
``` or go into System/Administration/Log File Viewer and look in dmesg and kern.0.log; hopefully there'll be something complaining.

If you need more help, given that partitions are most likely to be your problem, ```
cat /etc/fstab
``` in a terminal might tell you more; post back the output if you need more help.

---

