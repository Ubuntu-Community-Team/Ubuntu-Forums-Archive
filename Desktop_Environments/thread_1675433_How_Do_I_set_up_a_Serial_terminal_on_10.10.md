---
title: "How Do I set up a Serial terminal on 10.10?"
date: 2011-01-25
forum: Desktop Environments
---

### Post by toml_12953 on 2011-01-25
I've been trying to use a Teletype ASR-33 terminal to log into Ubuntu 10.10 with no luck.  I have the following file, called ttyS0, in /etc/init/jobs.d *and* in /etc/init/event.d:
 
# ttyS0 - getty
#
# This service maintains a getty on ttyS0 from the point the system is
# started until it is shut down again.
start on stopped rc2
start on stopped rc3
start on stopped rc4
start on stopped rc5
stop on runlevel 0
stop on runlevel 1
stop on runlevel 6
respawn
exec /sbin/getty -L 110 ttyS0
 
Neither is seen when I start Ubuntu.  When I run the ttyS0 file manually, I get a number of errors:
 
start: Unknown job: on
start: Unknown job: on
start: Unknown job: on
start: Unknown job: on
stop: Unknown job: on
stop: Unknown job: on
stop: Unknown job: on
./ttyS0: 15: respawn: not found

Is there a way to use a serial terminal in 10.10?  If so, how??? :icon_frown:

---

