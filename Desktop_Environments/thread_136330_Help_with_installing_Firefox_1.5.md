---
title: "Help with installing Firefox 1.5"
date: 2006-02-25
forum: Desktop Environments
---

### Post by jhaykage on 2006-02-25
I need help with installing Firefox 1.5.0.1 in my Ubuntu machine.

I already visited the Wiki and followed the exact directions but when I enter the tar command I get this error message:

tar: firefox-1.5.0.1.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

What should I do to fix this? Help, anyone...:confused:

---

### Post by aysiu on 2006-02-25
This ```
tar: firefox-1.5.0.1.tar.gz: Cannot open: No such file or directory
``` usually means you're not in the right directory. If you downloaded the .tar.gz to your desktop, you may have to do this first: ```
cd Desktop
``` before un-tarring it.

---

