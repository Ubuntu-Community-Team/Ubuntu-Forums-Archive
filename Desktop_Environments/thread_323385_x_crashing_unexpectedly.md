---
title: "x crashing unexpectedly"
date: 2006-12-22
forum: Desktop Environments
---

### Post by felipe1982 on 2006-12-22
Pentium 3 800 Mhz, 384mb RAM, 120 GB hd, one partition with ubuntu edgy installed.

Installed ubuntu this morning, ran some updates ---- X crashed, and logged me out of my session. The screen goes blank except for a blinking cursor Top Left corner of the screen. The login window comes back. I log in, continue to update, surf the web, check mail - CRASH! Logs me out - same cycle. I successfully installed some updates that contained words like "X" and "xorg" and "gnome" and "desktop". Rebooted and problem remains. 

Video Card : "3Dfx Interactive, In.c Voodoo 3"
How do I stop this from happening? Should I post contents of xorg.conf? OMG!! It just crashed again (currently running two machines simultaneously to watch what happens and report immediately)

Typing "tail -f /var/log/messages" shows this:
```
Dec 22 01:29:33 anarchy gconfd (felipe-11746): Received signal 15, shutting down cleanly
``` It shows much more, but that seemed interesting (anarchy is my computer/host name). All i did was type "sudo dpkg --configure -a" in a terminal, and CRASH! after attempting to upgrade "vino" package. What the heck is going on?!?](*,)

---

### Post by felipe1982 on 2006-12-22
Here are the outputs of some log files. The crash happened again at **11:44 EST** and again 5 minutes later at **11:49 EST**.

daemon.log
```

Dec 22 02:12:10 anarchy init: tty6 process (3563) killed by signal 15
Dec 22 02:47:27 anarchy gdm[3982]: Couldn't authenticate user
Dec 22 02:55:19 anarchy init: tty3 process ended, respawning
Dec 22 03:01:40 anarchy rpc.statd[5581]: Version 1.0.9 Starting
Dec 22 11:44:54 anarchy gdm[3982]: Error reinitilizing server
Dec 22 11:49:22 anarchy gdm[18890]: Error reinitilizing server
Dec 22 11:50:28 anarchy gdm[19238]: Error reinitilizing server
```


/var/log/messages
```

Dec 22 11:45:04 anarchy gconfd (felipe-4418): GConf server is not in use, shutting down.
Dec 22 11:45:04 anarchy gconfd (felipe-4418): Exiting
Dec 22 11:45:24 anarchy gconfd (felipe-18949): starting (version 2.16.0), pid 18949 user 'felipe'
Dec 22 11:45:24 anarchy gconfd (felipe-18949): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Dec 22 11:45:24 anarchy gconfd (felipe-18949): Resolved address "xml:readwrite:/home/felipe/.gconf" to a writable configuration source at position 1
Dec 22 11:45:24 anarchy gconfd (felipe-18949): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Dec 22 11:45:24 anarchy gconfd (felipe-18949): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Dec 22 11:45:24 anarchy gconfd (felipe-18949): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Dec 22 11:45:29 anarchy gconfd (felipe-18949): Resolved address "xml:readwrite:/home/felipe/.gconf" to a writable configuration source at position 0
Dec 22 11:49:21 anarchy gconfd (felipe-18949): Received signal 15, shutting down cleanly
Dec 22 11:49:21 anarchy gconfd (felipe-18949): Exiting
Dec 22 11:49:31 anarchy gconfd (felipe-19297): starting (version 2.16.0), pid 19297 user 'felipe'
Dec 22 11:49:31 anarchy gconfd (felipe-19297): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Dec 22 11:49:31 anarchy gconfd (felipe-19297): Resolved address "xml:readwrite:/home/felipe/.gconf" to a writable configuration source at position 1
Dec 22 11:49:31 anarchy gconfd (felipe-19297): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Dec 22 11:49:31 anarchy gconfd (felipe-19297): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Dec 22 11:49:31 anarchy gconfd (felipe-19297): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Dec 22 11:49:36 anarchy gconfd (felipe-19297): Resolved address "xml:readwrite:/home/felipe/.gconf" to a writable configuration source at position 0
Dec 22 11:50:27 anarchy gconfd (felipe-19297): Received signal 15, shutting down cleanly
Dec 22 11:50:27 anarchy gconfd (felipe-19297): Exiting
Dec 22 11:50:41 anarchy gconfd (felipe-19556): starting (version 2.16.0), pid 19556 user 'felipe'
Dec 22 11:50:41 anarchy gconfd (felipe-19556): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Dec 22 11:50:41 anarchy gconfd (felipe-19556): Resolved address "xml:readwrite:/home/felipe/.gconf" to a writable configuration source at position 1
Dec 22 11:50:41 anarchy gconfd (felipe-19556): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Dec 22 11:50:41 anarchy gconfd (felipe-19556): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Dec 22 11:50:41 anarchy gconfd (felipe-19556): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Dec 22 11:50:45 anarchy gconfd (felipe-19556): Resolved address "xml:readwrite:/home/felipe/.gconf" to a writable configuration source at position 0
```

"tail" of Xorg.0.log
```
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
AUDIT: Fri Dec 22 11:50:31 2006: 19498 X: client 2 rejected from local host
AUDIT: Fri Dec 22 11:50:31 2006: 19498 X: client 4 rejected from local host
AUDIT: Fri Dec 22 11:50:31 2006: 19498 X: client 3 rejected from local host
```

---

### Post by felipe1982 on 2006-12-26
can anyone help! please?

---

### Post by Tteddo on 2007-03-21
I am having the same problem with a P4 1800 GeForce 100 machine. It is happening randomely while the sceensaver is one, altho not nearly as often as Felipe. Maybe once a day.
Here are some relevant log entries:

> daemon log: Mar 21 09:35:05 Vishnu gdm[23931]: Error reinitilizing server

messages: Mar 21 09:34:57 Vishnu gconfd (tteddo-11858): Received signal 15, shutting down cleanly
	Mar 21 09:35:02 Vishnu gconfd (tteddo-11858): Exiting

syslog: Mar 21 09:34:57 Vishnu gconfd (tteddo-11858): Received signal 15, shutting down cleanly
	Mar 21 09:35:02 Vishnu gconfd (tteddo-11858): Exiting
	Mar 21 09:35:05 Vishnu gdm[23931]: Error reinitilizing server


---

### Post by keller.baum on 2007-03-28
I am having the same problem on a ICH8R core 2.  I've been running feisty since rc3 without problems but now I'm getting random x crashes.  They seem to happen when i have multiple copies of firefox open.  I'm getting similar stuff in the system log:

Resolved address "xml:readonly:/etc/gconf/debian.defaults" to read only...

maybe this is a bug in gconf?

---

### Post by Tteddo on 2007-03-28
I also have multiple copies of Firefox open all the time.
I wish I could reproduce it. Of all the copies of Firefox I have open, only one window is updating constantly, about every 3 minutes, the rest are static.
I see a log entry like yours on a normal X startup for each user that is active (I have a VNC user that runs in the background for remote access to my network).

---

### Post by keller.baum on 2007-03-28
I was able to reproduce the error consistently.  Every time i go to [http://forums.techguy.org/unix-linux/493287-x-windows-error.html](http://forums.techguy.org/unix-linux/493287-x-windows-error.html) and scroll down x crashes.  I just tried reverting kernels back to 2.6.20-11 from -13 and x hasn't crashed yet.  This may be a band-aid for now but the problem still exists.

---

### Post by Tteddo on 2007-03-28
Mine doesn't crash on that page, Hmm..... Mine crashes out when I am not using it, I disabled the random screensaver a day ago and it's been fine, but sometimes it would go 3 or 4 days and not boot me out to the login screen. I guess i should stick with the blank screen for awhile and see if that is it in my situation because changing more than one thing at once will confuse the issue. I'll post back in a couple of days...

---

