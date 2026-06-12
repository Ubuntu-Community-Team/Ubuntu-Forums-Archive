---
title: "(really) bad Performance on Inspiron, maybe disk-related"
date: 2008-03-24
forum: Dell  Ubuntu Support
---

### Post by elTigre on 2008-03-24
I am running Ubuntu Gutsy on an Inspiron 6400 Laptop from Dell.
The last three weeks or so performance got very bad in certain tasks, like text editing and startup. It takes Gnome about 5-6 minutes to be usable and I am talking about a Dualcore system with 2 Gb ram.

I monitored the startup process by running top in a console. I found beagled, trackerd and Gnomepanel to be at the top at all times, though they hardly consume any CPU time.

But the "wait" portion of system IO is between 50 and 80 %. So I am guessing it has something to do with disk IO.

I am using a text editor called scribes. And there it is a little painful, as I sometimes have to wait a few seconds after saving. I never had this issue on a very less modern system, and Scribes, even though it is a Python program, shouldn't be that much of a challenge for my system.

I couldn't figure out how to use hdparm for SCSI system, and the usual performance "tweaks" I found in google did not resolve the issue.

I would appreciate it, if somebody could point out an angle I could try.

Thanks!

---

### Post by elTigre on 2008-03-25
Hm no Idea? I still can't solve the issue.

---

