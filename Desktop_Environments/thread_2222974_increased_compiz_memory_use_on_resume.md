---
title: "increased compiz memory use on resume"
date: 2014-05-08
forum: Desktop Environments
---

### Post by zeke2135 on 2014-05-08
I've noticed for some time that compiz seems to increase its memory use over time (this was true since 13.10 when I first installed ubuntu on my machines). It seems like compiz increases its memory use dramatically when my computer resumes from suspend mode. 
For example in a recent test:
I logged on, at which time compiz memory use was reported as 46MiB in System Monitor.
I did nothing (except run System Monitor to check memory use), let the computer enter suspend mode (I use powernap), and when I woke the computer up, System Monitor reported that compiz was using 223MiB.

The other effect I see is that when the computer resumes, the unity launcher, top panel, and indicator area in the upper right, are not rendered. I see what looks like random pixel coloring in those areas (sometimes not all three show this effect).  This persists until I mouse over the top panel or click in the other areas, or I can hit the "super" key which causes the dash to open up, and the other areas to be redrawn. I'm wondering if this is related to the compiz issue.

I'd like to know if this is a known bug (I haven't found any similar description thru google) and/or if anyone has any remedy.

I'm using ubuntu 14.04 w/ unity and nvidia proprietary driver. This is on a home-built computer w/ asus motherboard, amd athlon X4 740 processor, and nvidia 8400GS-based graphics card.

---

### Post by buzzingrobot on 2014-05-11
I'll bump this to say, yes, I see it here.  (May be this confirmed bug:  [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1314787](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1314787))

On a fresh 14.04 install, on a fresh login, with 4 empty workspaces, compiz is at 99 MiB.  That increases marginally when an app is opened in each workspace.  After suspending and resuming 30 minutes later, compiz is at 209 MiB.  After suspending overnight, compiz is at 444 MiB immediately after resume.

---

### Post by zeke2135 on 2014-05-11
The bug in the link sounds different to me. Memory increased without doing anything in that case, and much more severely?

In addition to an increase on suspend/resume, I noticed that memory use increases when switching users (and/or when running system monitor from the dash), but not consistently. It tends to go up but sometimes comes partially back down. Finally, after testing by switching back and forth between two users about ten times, the user interface became quite sluggish, and only partly responsive. BTW I believe that Xorg increases its memory use as well but I haven't really focused on that. 

Actually, I've had problems in the past w/ switching users. In 13.10, Xorg would crash quite often when I switched users.

---

### Post by speartip on 2014-06-24
I know this thread is now 6 weeks old, but does anyone yet have any solutions/answers to this issue.
After login my compiz uses 60-80mb memory, but once I open any application from the dash or search using the dash memory jumps to about 250mb, & will steadily increase to around 400-500mb, before I either logout or reboot.

---

### Post by Roo8choo on 2014-06-24
> **speartip said:**
> I know this thread is now 6 weeks old, but does anyone yet have any solutions/answers to this issue.
After login my compiz uses 60-80mb memory, but once I open any  application from the dash or search using the dash memory jumps to about  250mb, & will steadily increase to around 400-500mb, before I  either logout or reboot.
I have the same issue with Compiz and Xorg on my desktop. I'm also using a Nvidia card with the proprietary driver.

---

### Post by speartip on 2014-06-25
I do not have a nvidia card, mine is just an Intel integrated graphics card using the open source drivers, so I do not think this problem is Nvidia specific.

---

### Post by Roo8choo on 2014-06-30
> **speartip said:**
> I do not have a nvidia card, mine is just an Intel integrated graphics card using the open source drivers, so I do not think this problem is Nvidia specific.Strange, I'm also using a Intel card in my Acer laptop but I don't experience any problems on that machine. Only my desktop has this issue. ;)

---

### Post by slonk on 2014-06-30
There is a lot more physical memory free after waking up on resume because all cache pages have been purged.  Furthermore, parts of it might have been in paging space and might now be back in RAM. Would be useful to know what your paging space usage before/after suspend it.

I wouldn't see this as an alarm sign unless it is later causing actual memory stress.  Trying writing a large file so that a lot of RAM is used for the write cache and see whether that makes it shrink again.

---

### Post by startas on 2014-06-30
No suspend needed, over 200 mb for compiz is really hunger for memory for something that it is and what it does, maybe it has huge memory leaks.

---

