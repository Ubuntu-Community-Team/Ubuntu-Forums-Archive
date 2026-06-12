---
title: "soffice.bin showing up in conky, but not top?"
date: 2011-12-13
forum: Desktop Environments
---

### Post by tiger63 on 2011-12-13
Weird stuff going on here.  Every day soffice.bin eventually shows up in my conky under memory-consuming processes (see screenshot).  It's not there when I boot up and not there most of the day...but every afternoon it suddenly appears.  I haven't used Libre Office in weeks, so that is confusing.  Here's the weird part:  When I try to do sudo killall soffice.bin in a terminal, I get "soffice.bin: no process found."  Also isn't found in top.  

So, I opened the task manager and it was there (PID 1071, owner root).  So I opened a sudo taskmanager and it was NOT there.  This really has me baffled.  Anyone have any explanation?

[IMG]http://img39.imageshack.us/img39/1053/sofficeh.png[/IMG]

---

