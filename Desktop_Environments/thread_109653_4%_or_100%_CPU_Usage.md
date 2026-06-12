---
title: "4% or 100% CPU Usage"
date: 2005-12-29
forum: Desktop Environments
---

### Post by andrewsawyer on 2005-12-29
Please see the attached screenshots...

They are both from the sytem monitor on my Breezy system.  The first shows all the programs that are using resources, with the highest at the top.  It shows a total of 4% CPU usage.  The second is taken just after from the Resources tab on the same system.  This shows a constant usage of 100%.  I would say from the speed of the system (or rather lack of it) that the latter 100% usage is the correct.

Can someone please shed some light on why whatever is chewing my CPU is not listing in the Processes section of System Monitor, and also how I might find out what it is and how I might turn it off?

Rebooting will leave the system ok for a while, however then it will jump back to the 100% usage in the Resources tab.  This is obviously very frustrating, as it means constant reboots.  This machine sits under my tv in the living room, and is just used for media.  I installed apache and mysql on it, but then later uninstalled them.

Any help would be much appreciated.

Andy

---

### Post by towsonu2003 on 2005-12-29
try View>All Processes

you can also try ```
top
``` from the terminal.

---

### Post by andrewsawyer on 2005-12-29
Thank you!

Typing 'top' from the command line showed the process to be clamscan which was running from root.  I remember I set it to scan in my cron settings, but I don't actually know how to turn it off.  Can you help?

---

### Post by ed_d on 2005-12-29
Could always just dd the line in cron......

Or see if the software is installed and try removing it too.

---

### Post by towsonu2003 on 2005-12-30
as the job is running as root (why?) ```
sudo crontab -e
``` and delete the line about clamscan (if the line is not there, I have no idea)

---

