---
title: "Very slow to respond after resizing any window"
date: 2008-02-19
forum: Desktop Environments
---

### Post by cebo0650 on 2008-02-19
I'm running Ubuntu Gutsy with Compiz on a ThinkPad T41p with an ATI graphics card. I'm using the fglrx drivers.

Everything, including all the 3D desktop effects run fast and smooth, but as soon as I resize ANY window by clicking on the corner or side and dragging, the computer slows down to a crawl and becomes very unresponsive. The only way to recover from this is to restart.

Has anyone experienced this before, and if so is there a fix? :confused:

---

### Post by cebo0650 on 2008-02-24
Any one? Am I the only one with this issue?

---

### Post by oceanexplorer on 2008-02-24
Just to let you now you are not alone, I also get the issue, fairly new to Ubuntu so don't have the answer! I'm also running an ATI card with Compiz-Fusion enabled, everything runs great except for when I resize a window, the system grinds to a halt.

If I come up with an answer I will let you know. 

Paul

---

### Post by nuclearpenguin on 2008-02-26
Same thing here on a T60 thinkpad with Centrino Duo CPU, 1.5 gig ram and 512mb ATI x1300go.

This is a fresh install and seems to work flawlessly other than that.  I whitelisted the fglrx driver and have been searching for answers...

---

### Post by nuclearpenguin on 2008-02-26
I found it:
[http://ubuntuforums.org/showthread.php?t=625682&highlight=compiz+slow+resize](http://ubuntuforums.org/showthread.php?t=625682&highlight=compiz+slow+resize)

---

### Post by oceanexplorer on 2008-02-28
Thanks for the link, I will give that a go tonight and see how it goes.

Paul

---

### Post by oceanexplorer on 2008-02-28
Thanks that link worked a treat, greatly appreciated.

For others who view this, I went into CCSM, then under the section Uncatergorized selected the option resize window, then changed the default to stretch rather than rectangle.

Paul

---

