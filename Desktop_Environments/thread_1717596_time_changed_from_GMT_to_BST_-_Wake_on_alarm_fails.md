---
title: "time changed from GMT to BST - Wake on alarm fails"
date: 2011-03-30
forum: Desktop Environments
---

### Post by mister_p_1998 on 2011-03-30
Ok, I'm running Ubuntu Hardy 8.04 and in the UK we changed from GMT to BST last Sunday (27th March)
On GMT I was waking on LAN at 23:30, all was working fine then we changed to BST. What I usually do is leave the BIOS clock on GMT and change the Wake on Alarm to 22:30. I did this, shut down Ubuntu fine, but its not waking up at all at 22:30, or any other time I set the WOA to. I had this problem a few years ago on an old ASrock mobo and cant remember how I sorted it - maybe by blanking the bios, cant remember. Any ideas guys?

Steve

---

### Post by mister_p_1998 on 2011-03-30
Would this work I wonder?

Disable HWclock updates

The reason for this recommendation is that most Linux distributions write the current system time back to the BIOS when shutting down the machine. With most BIOS, the machine will not wake up if the hardware clock has been modified after the wakeup alarm has been set. To avoid this, it is necessary to disable the writing of the current system time to the BIOS by the system shutdown scripts. 

Debian (and Ubuntu 8.04 and earlier)

Set HWCLOCKACCESS to "no" in /etc/default/rcS
Image:Script.png /etc/default/rcS

#
# /etc/default/rcS
#
# Default settings for the scripts in /etc/rcS.d/
#
# For information about these variables see the rcS(5) manual page.
#
# This file belongs to the "initscripts" package.

TMPTIME=0
SULOGIN=no
DELAYLOGIN=no
UTC=no   (Default is Yes)
VERBOSE=no
FSCKFIX=no
HWCLOCKACCESS=no

Im going to try this tonight when I get home, sounds promising.

Steve

---

### Post by mister_p_1998 on 2011-03-30
Didnt work.. I also noticed that if I cat /proc/driver/rtc
Alarm is still 23:30:00 how come? I changed it in the bios to 22:30:00
See below:

rtc_time	: 17:09:46
rtc_date	: 2011-03-30
rtc_epoch	: 1900
alarm		: 23:30:00
DST_enable	: no
BCD		: yes
24hr		: yes
square_wave	: no
alarm_IRQ	: no
update_IRQ	: no
periodic_IRQ	: no
periodic_freq	: 1024
batt_status	: okay

Steve

---

### Post by mister_p_1998 on 2011-03-31
Pulled the battery out all setting back to factory, still wont WOA!
Whats changed? it worked fine since July 2010, all I did was change the startup time from 23:30 to 22:30!

---

### Post by mister_p_1998 on 2011-04-04
Sorted!
this seemed to do the job -

sudo sh -c 'echo "00-00-00 22:30:00" > /proc/acpi/alarm'

This tells the system to write the above to the bios - wake up every year, every month, every day at 22:30 UTC. This works for April, I'm hoping it carries through to the rest of the year. I left the BIOS time on UTC and told the system to wake at 22:30 UTC (23:00 BST) If all is well after April, I'll mark this as solved.

BTW if you're using a later Distro than 8.04 the place to write the alarm data is: /sys/class/rtc/rtc0/wakealarm'
FULL command: sudo sh -c 'echo "00-00-00 22:30:00" > /sys/class/rtc/rtc0/wakealarm'
Steve

---

