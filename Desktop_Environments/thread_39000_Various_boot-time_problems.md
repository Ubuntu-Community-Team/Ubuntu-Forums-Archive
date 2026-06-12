---
title: "Various boot-time problems"
date: 2005-06-03
forum: Desktop Environments
---

### Post by Cordate on 2005-06-03
i've been getting 3 errors during boot-up and though I've reinstalled the packages that seem to be related to the errors, I am still getting them. This makes me think that maybe they are related somehow...

The first error shows up as this in my boot sequence series of messages:
```
Synchronizing clock to ntp.ubuntulinux.org...
/etc/rcS.d/S51ntpdate: line 17: 5364 Segmentation Fault 
/usr/sbin/ntpdate -b -s $NTPOPTIONS $NTP SERVERS
```

and the second:
```
Starting GNOME display manager...
/etc/rc2.d/S13gdm: line 43 5625 Segmentation Fault 
start-stop-daemon --stt --quiet --pidfile $PIDFILE --name gdm 
$SSD_ARG >/dev/null 2>&1
```

and the third:
```
Starting Hardware abstraction layer
/etc/dbus-1/event.d/20hal: line 31 5823 Segmentation Fault 
start-stop-daemon --start --pidfile $PIDFILE --exec $DAEMON --$DAEMON_OPTS
run-parts ./etc/dbus-1/event.d/20hal exited with return code 139
```

I copied these by hand, so there may be typos in there. I couldn't find these messages showing up in any of the /var/log files or I'd have cut-n-pasted. 

I am pretty sure that the Segmentation Faults were happening from disk corruption coming from bad RAM, but I've pulled one of my sticks of RAM out and it seems like I ought to be able to at least temporarily repair these errors. I've run a fsck on the / partition and it went through and fixed several problems, but I still can't seem to change these errors.  I've reinstalled gdm, gnome, & ntpdate but everything seems to still be happening the same way.

I can post the contents of the files if that will help. The line numbers in the error messages seem to refer to innocuous-looking lines of code- two of them are simply
```

case "$1" in
```
and nothing else... so I don't know if it's actually these files causing the issues?

Thanks in advance for any help!

-Cordate

---

### Post by az on 2005-06-03
With bad ram, any piece of installed software may be corrupted, since it may have been silently broken during the install.

I would make a backup of my data and reinstall with working ram.  You may spend weeks hunting down broken libraries.

Do not discard your bad ram.  There is a badram patch that applies to the Hoary kernel.  You can scan your ram and use the good parts of the stick!  You cannot do that on windows!

---

### Post by Cordate on 2005-06-05
Thanks Azz! I've reinstalled with the bad stick pulled and things went the way they ought to for once :) I'm working on getting the memory exchanged where I bought it but if that doesn't work out for some reason I will look into telling Ubuntu to use just the good parts.

-Cordate

---

