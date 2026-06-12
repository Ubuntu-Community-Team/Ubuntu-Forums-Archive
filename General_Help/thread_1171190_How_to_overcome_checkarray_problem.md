---
title: "How to overcome checkarray problem"
date: 2009-05-27
forum: General Help
---

### Post by R3d3agl3 on 2009-05-27
Hello everyone,

I have a Ubuntu system that uses 3 discs at work. 2 of the discs use raid 1 and the 3rd one uses raid 5.
The mdadm cron task that executes "/usr/share/mdadm/checkarray --cron --all --quiet" at 1:06 AM of the first sunday of every month, crashes my system everytime. On the following monday morning, when I arrive at work I see the status LED on the machine, red.
From what I've seen, this is a common problem and I seriously doubt that there is something wrong with any of my discs, because they are new, and work perfectly the rest of the month ;)
I've tried to comment out the execution of the checkarray task, but something unexpected happended. What happened was that everyday at 1:06 AM the system became unreponsive, and despite I could see the authentication screen, I was unable to login. Another thing, the status LED on this case was green. This happened on the 20rd of May so why did this happen? When I uncommented the line, to it's original state the system didn't staul, but I know it will happen again next month.
I have VMWare installed and running 2 VM's... Could that have anything to do with the problem?
Any help would be very much appreciated on this problem.

Thanks

---

### Post by R3d3agl3 on 2009-05-27
By the way these are the parameters that the check takes into account:


**-cron -> honour AUTOCHECK setting in /etc/default/mdadm.**

_/etc/default/mdadm_

[I]# mdadm Debian configuration
#
# You can run 'dpkg-reconfigure mdadm' to modify the values in this file, if
# you want. You can also change the values here and changes will be preserved.
# Do note that only the values are preserved; the rest of the file is
# rewritten.
#

# AUTOCHECK:
#   should mdadm run periodic redundancy checks over your arrays? See
#   /etc/cron.d/mdadm.
AUTOCHECK=true

# START_DAEMON:
#   should mdadm start the MD monitoring daemon during boot?
START_DAEMON=true

# DAEMON_OPTIONS:
#   additional options to pass to the daemon.
DAEMON_OPTIONS="--syslog"

# VERBOSE:
#   if this variable is set to true, mdadm will be a little more verbose e.g.
#   when creating the initramfs.
VERBOSE=false

# MAIL_TO:
#   this variable is now managed in /etc/mdadm/mdadm.conf (MAILADDR).
#   Please see mdadm.conf(5).[/I]


**-all -> check all assembled arrays (check /proc/mdstat)**

_/proc/mdstat:_

[I]Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md2 : active raid5 sda3[0] sdc3[2] sdb3[1]
      410267776 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]

md3 : active raid1 sda2[0] sdc2[2](S) sdb2[1]
      7815552 blocks [2/2] [UU]

md0 : active raid1 sda1[0] sdc1[2](S) sdb1[1]
      31246272 blocks [2/2] [UU]

unused devices: <none>[/I]


**-quiet -> suppress informational messages.**


In light of this information, how do you recomend I solve this problem? I would bet on setting the AUTOCHECK variable to false, but some feedback on this would be very much appreciated ;)

---

### Post by R3d3agl3 on 2009-05-29
Sorry for the persistence, but some feedback on this subject would be very much appreciated, even if it's a negative :p

Thanks once again

---

### Post by ronparent on 2009-05-29
You might want to check launchpad to see if there is record of simular problems. Also you might want to repost in the server section of this forum in which users would likely have a better understanding of raid arrays in general. I regret that I can't be more helpful but I hope these comments are of some help to you.

---

### Post by R3d3agl3 on 2009-05-29
Thanks for the response ronparent.

I'll follow your recomendations and see if I have more luck...

---

### Post by enrico.simonetti on 2010-05-01
Hi there,

Any luck on this yet?

I run OpenVZ on hardy (2.6.24-27-openvz and 2.6.24-26-openvz) on 2 different servers.
They both keep crashing.

Is this related to bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/212684](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/212684) ?

Thanks

---

