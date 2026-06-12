---
title: "Burning ISO images at the command line"
date: 2006-08-15
forum: Desktop Environments
---

### Post by randysparks on 2006-08-15
I've got a Plextor DVD+-R/RW drive and I'd like to use it to burn CD ISO images from the command-line, via cdrecord. For some reason, 

sudo cdrecord -scanbus

isn't discovering it. I'm told there's nothing present on the system. On distros like SUSE Linux, other commands are used if DVD writer drives are in operation, such as cdrecord-dvd. 

Does Ubuntu have an equivalent? growisofs appears to be only for burning DVDs, not CDs.

---

### Post by randysparks on 2006-08-15
It's OK, I figured it out. Seems I'm a little out of date when trying to specify a device number. Nowadays you can specify /dev/hdc, so the -scanbus command option isn't needed.  ;)

---

