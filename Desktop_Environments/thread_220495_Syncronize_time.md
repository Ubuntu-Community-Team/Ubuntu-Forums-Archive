---
title: "Syncronize time"
date: 2006-07-21
forum: Desktop Environments
---

### Post by leaded on 2006-07-21
What is the command line equivilant to right-clicking on the time in Gnome, Choosing Adjust Date & Time, and clicking Synchronize Now?

I have Dapper Server (with ubuntu-desktop installed later) running on a Mac mini and it loses several minutes of time per day. I have checked the box to Periodically synchronize clock with Internet servers, but it doesn't seem to ever syncronize that I can tell. I left the computer alone for 2 weeks and it lost about 30 minutes of time.

So far, the only way I know to fix the clock is to run the date -s "2006/07/dd HH:MM:SS" (with numbers, of course) command but it doesn't keep. If I can find the command-line version of synchronzing the time, I can set it up as a cronjob every night.

Can someone help me out? If that doesn't work, what else should I do?

---

### Post by Dubbayoo on 2006-07-21
sudo ntpdate tick.cs.unlv.edu

---

### Post by carlosqueso on 2006-08-03
I'd use pool.ntp.org instead.

---

### Post by leaded on 2006-08-03
I ended up using the north american pool.

---

