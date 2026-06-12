---
title: "&quot;Access external storage devices automatically&quot; privilege has no effect"
date: 2008-07-20
forum: Desktop Environments
---

### Post by sleepya on 2008-07-20
I tried to create a new user, named test1, on Ubuntu 8.04.1. While creating, I unchecked the "Access external storage devices automatically" and "Use CD-ROM drives" privileges.

When I logged on with the new user (test1), I still can use usb flash drive and cdrom.

Does anyone have any idea?

---

### Post by jmr on 2010-12-17
I just found this out today, much to my surprise, on an ubuntu 9.10 system, and also on a 10.04.  It seems to work on a 6.06.

I made sure and verified that the user I created did not belong to the plugdev group (or any other group beyond the user's own group).  When I plugged a USB drive it was mounted immediately.  Apparently, membership in plugdev group is not required, defeating its purpose.

I know people are generally worried about not being able to mount USB drives, but this is just the opposite: we can mount USB drives, but shouldn't be able to!

I think it must be HAL/udev (or something like that) that is configured to "ease" things for the end user, but disregards security issues.

I'll check it further.  It might be considered a bug.

João Rodrigues

---

