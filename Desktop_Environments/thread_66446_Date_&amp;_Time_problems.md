---
title: "Date &amp; Time problems"
date: 2005-09-17
forum: Desktop Environments
---

### Post by DeadEyes on 2005-09-17
Hi all,
I've had ubuntu on my machine now for a couple of weeks and I must say I'm impressed. I've installed a number of different distros but this is the first one I feel I can actual use. I'm still having problems though a few actually but I'll keep it one per post :smile:

I've got dual boot XP/Unbuntu but the time keeps getting messed up between the two.

I log into windows I have the time set correctly and is GMT.
I log into linux the timezone is Europe/Dublin (ie GMT) but the time is out by an hour.
If I correct the time in linux and boot back to windows then the windows time is out by an hour.

When I boot linux it tries to synch with a time server but I don't have internet access from linux (wifi problems but thats for another day).

Does anyone have any ideas what's going on or how to fix it?

---

### Post by Irony on 2005-09-17
I had the same problem which I solved, a long forum search came up with;

[I]sudo cp /etc/default/rcS /etc/default/rcS_backup

sudo gedit /etc/default/rcS[/I]

Change;

[I]# Set UTC=yes if your system clock is set to UTC (GMT), and UTC=no if not.
UTC=yes[/I]

To;

[I]# Set UTC=yes if your system clock is set to UTC (GMT), and UTC=no if not.
UTC=no[/I]

In other words first you back-up your rcS file then you alter it. My file now looks like this;

[PHP]#
#	Defaults for the boot scripts in /etc/rcS.d
#

# Time files in /tmp are kept in days.
TMPTIME=0
# Set to yes if you want sulogin to be spawned on bootup
SULOGIN=no
# Set to no if you want to be able to login over telnet/rlogin
# before system startup is complete (as soon as inetd is started)
DELAYLOGIN=no
# Set UTC=yes if your system clock is set to UTC (GMT), and UTC=no if not.
UTC=no
# Set VERBOSE to "no" if you would like a more quiet bootup.
VERBOSE=no
# Set EDITMOTD to "no" if you don't want /etc/motd to be editted automatically
EDITMOTD=yes
# Set FSCKFIX to "yes" if you want to add "-y" to the fsck at startup.
FSCKFIX=no[/PHP]

I think the reason it was off in the first place is that when I installed ubuntu I select yes when it asked if my clock was UTC.

---

### Post by DeadEyes on 2005-09-18
Thanks Irony that fixed my problem.

---

