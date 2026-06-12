---
title: "How do I start diagnosing a crash?"
date: 2009-01-29
forum: General Help
---

### Post by deltaromeo on 2009-01-29
Ubuntu 8.04 has been crashing recently.  ctrl-alt-backspace doesn't help and alt-sysreq REISUB does nothing.  It's a complete freeze.  I have to use the power button to reboot.

Please can you point me in the right direction in an attempt to find the source of the crash?  Any pointers would be appreciated.

Thank you.

---

### Post by khedron on 2009-01-29
Ok, system messages are stored in **/var/log/syslog**. You are looking for error messages that pop up just before your last boot, so search backwards in the file for a line looking like this:
```
Jan 28 07:36:29 wyenet syslogd 1.5.0#2ubuntu6: restart.
``` and work backwards from there.
If syslog only has the messages for the current boot, try **/var/log/syslog.0** . This is the previous syslog file - they get changed regularly.

For problems regarding X11, try **/var/log/Xorg.0.log**.

Essentially look in /var/log and try any files that look promising to check for problems.

Regarding the first comment about searching backwards through **/var/log/syslog**, I'll go through it stepwise if you need. Open it with less:
```
less /var/log/syslog
```Then go to the end of the file by typing **G** (that's a capital g).
Then type ```
?syslog.*restart
``` to go to the last restart. Then go up the file (with the arrow keys ;) ) and look for error messages.

Does that help?

---

### Post by khedron on 2009-01-29
Also, from what you have said it looks like it might even be a kernel panic, so you can also look in **/var/log/kern.log** . Use the backward searching technique like for **/var/log/syslog**, except search backward for "000000" (six zeroes) as that is always printed out shortly after the computer has started.

You can see exactly when the restart was by looking at the times given and looking for gaps in the time - those show gaps when the computer was not responsive (or off!).

---

### Post by deltaromeo on 2009-01-29
Thanks mate, that looks like it will be helpful.  Will check as soon as I am back at my PC.

---

### Post by deltaromeo on 2009-01-29
Thanks for you help this far, you have already taught me how to search using less and what to search for to find the reboot points.

syslog has this before the crash:

```

Jan 29 19:27:55 dmt NetworkManager: <debug> [1233257275.096056] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_54c_325_4
92427072333'). 
Jan 29 19:42:56 dmt -- MARK --
Jan 29 19:46:24 dmt ntpd[4105]: synchronized to 130.88.202.49, stratum 2
Jan 29 19:51:48 dmt ntpd[4105]: synchronized to 130.88.200.4, stratum 2
Jan 29 19:55:34 dmt ntpd[4105]: synchronized to 130.88.202.49, stratum 2
Jan 29 20:02:28 dmt syslogd 1.5.0#1ubuntu1: restart.

```

not sure what all the "stratum 2" stuff is.

kern.log has the following:

```
Jan 29 19:03:05 dmt kernel: [38440.867033] audit(1233255785.203:9): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pi
d=11808 profile="/usr/sbin/cupsd" namespace="default"
Jan 29 19:27:54 dmt kernel: [39929.665171] usb 5-2: USB disconnect, address 2
Jan 29 20:02:28 dmt kernel: Inspecting /boot/System.map-2.6.24-23-generic
Jan 29 20:02:28 dmt kernel: Loaded 27898 symbols from /boot/System.map-2.6.24-23-generic.
Jan 29 20:02:28 dmt kernel: Symbols match kernel version 2.6.24.
Jan 29 20:02:28 dmt kernel: Loaded 17733 symbols from 89 modules.
Jan 29 20:02:28 dmt kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan 29 20:02:28 dmt kernel: [    0.000000] Initializing cgroup subsys cpu
Jan 29 20:02:28 dmt kernel: [    0.000000] Linux version 2.6.24-23-generic (buildd@palmer) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Thu Nov 27 18:44:42 UTC 
2008 (Ubuntu 2.6.24-23.46-generic)
```

Does anything there stick out?

---

### Post by khedron on 2009-01-30
Not that I can see. You are generally looking for obvious stuff, like error messages. Are there any things that you can do to cause it to freeze, or to be more likely to freeze?

It might also be a hardware problem, so you could try running Windows on it to see if it has any problems. If you have a temperature sensor in your case, see if anything is overheating.

---

### Post by hyper_ch on 2009-01-30
maybe there was also some kind of power fluctuation that did not turn the computer off but just left it in an unstable freezing stage... no clue really :(

---

