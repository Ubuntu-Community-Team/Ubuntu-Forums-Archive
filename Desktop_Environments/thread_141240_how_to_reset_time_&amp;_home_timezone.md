---
title: "how to reset time &amp; home timezone?"
date: 2006-03-07
forum: Desktop Environments
---

### Post by svref on 2006-03-07
I need to re-do the part of installation re: timezones, because the installer hinted darkly that **other operating systems** incorrectly handled the timezone.  As a result, Mac OS 10 thinks the system clock is set to GMT, Ubuntu thinks the system clock is set to local, and insanity ensues - 12 seconds after login the screen gets locked by XScreenSaver, and my wife is complaining.  Help!  

I can't call hwclock directly on this ibook: "Cannot access the Hardware Clock via any known method."

---

### Post by Xian on 2006-03-07
$ sudo tzconfig

From $ man tzconfig:

[i]" What timezone is correct for your system? It depends on the  geographi&#8208;
       cal  location  of  the machine.  Getting the correct location is impor&#8208;
       tant, but the system must also know how your  hardware  clock  is  set.
       Most  DOS  based PCs set their hardware clock on Local Time, while most
       UNIX systems set their hardware clock to UTC.

       The Debian GNU/Linux system gains its knowledge of  this  setting  from
       the file /etc/default/rcS.  This file contains either the line UTC=yes,
       which indicates that the hardware clock is set to UTC, or  it  contains
       the  line  UTC=no,  which  declares  the hardware clock is set to Local
       Time. If these setting are correct, and the hardware clock is truly set
       as indicated, then configuring the proper timezone for the machine will
       cause the proper date and time to be displayed. If these  are  not  set
       correctly,   the  the  reported  time  will  be  quite  incorrect.  See man
       hwclock for more details on this topic."[/i]

---

### Post by svref on 2006-03-07
hmm...post deleted

---

### Post by Xian on 2006-03-07
I thought you wanted to apply the tz and set the hwclock to UTC. No??

---

### Post by svref on 2006-03-13
Well, that did help somewhat, but I still have a serious problem.

Now when I login the time is slow by exactly N hours for some n in the 4-5 range.  After the first network connection is established (usually after gdm login thanks to Network Manager and wifi), the time jumps forward 5 hours.  The screensaver locks the screen.  The logfiles are ugly.  Life is bad.  :(

---

### Post by Xian on 2006-03-13
Here's a few ideas for you to try:

1. Use your sessions config to run a sync command like the one listed below. If you go this route you'll of course need to edit your sudoers file to allow this to be executed without your user passwd upon login to your desktop environment. Be sure to install rdate first as I don't believe it is on a default setup.

$ sudo rdate -s time-b.nist.gov

2. Make a runlevel script using the command above, or you can do the same with ntpdate (should already be installed). The script for ntpdate would need to look similar to the one below. 

#!/bin/sh
/usr/sbin/ntpdate us.pool.ntp.org
/sbin/hwclock -w

3. Make a cron job (daily) using either of the above methods.

---

### Post by svref on 2006-03-15
The built in time-syncer is what's syncing the clocks after the net connection is established.  The problem is not that.  The problem is, that before networking exists, that the time is very wrong.  Since this is an ibook, "hwclock" doesn't work.

---

