---
title: "15-20 sec pause after logging into Gnome... log I can look at?"
date: 2008-12-02
forum: Desktop Environments
---

### Post by graysky on 2008-12-02
Just installed Ibex amd64 on my system and am experiencing a 15-20 second pause after I log into Gnome.  First just the wallpaper, then the 'busy' mouse cursor.  When I boot into Debian/Lenny on the same machine, the desktop appear in about 5 sec.  What could be causing the slow down?  Is there a log file I can have a look at or...?

Thanks!

---

### Post by graysky on 2008-12-03
Does anyone else experience this running 8.10 for amd64?

---

### Post by Zorael on 2008-12-03
If you create a new dummy user, does it happen when logging in as it as well?

You may also want to go through Services (under Administration, I think?) and see if there's anything there that could stall things. Perhaps compare the list with your Debian installation and see what differs?

As for logs, I'm not sure to what extent Gnome logs; it would be placed in /var/logs/ if at all.

---

### Post by graysky on 2008-12-03
Thanks for the suggestion - I did create a fresh user account and indeed the slowdown is present.  I did notice quite a few startup programs compare to Lenny.

All I have under Lenny:

compiz-fusion
kerneloops
network manager
power manager
update notifier
volume manager

Under Ibex there were tons.  I did try disabling some, but found that I couldn't log into Gnome!  I wish Ubuntu was "lighter" than it is out-of-the-box like Lenny; I also wish Lenny had more up-to-date packages like Ubuntu does.  Guess you can't have it all :)

---

### Post by SmokinJuan on 2008-12-03
it's compiz-fusion.  but you don't want to turn that off, do you ;)

---

### Post by graysky on 2008-12-03
It's not compiz-fusion... wish there was a log file or something for trouble-shooting.

---

### Post by SmokinJuan on 2008-12-03
here's a stupid idea: add 
```
gnome-terminal -e top
```
to your System>Preferences>Sessions Startup Programs.  I you're lucky it'll launch a terminal with top running so you can see what process is bothering.

besides that, there *is* a log file under System>Administration>System Log. Have a look at the syslog, messages and others from the left pane.  This:
```
Nov 29 19:25:11 desktop kernel: [    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
```
is from the messages log, close to boot time.  The time of the log is shown far left and the [    0.000000] is a more accurate timer.  Whatever is causing you trouble should be logged.  After a fresh boot, check the log and note the differences between times.  The offending process is likely to have larger difference between its log time and the previous.  It will also be towards the bottom of the log.  Good luck.

---

### Post by graysky on 2008-12-04
Thanks for the suggestion... how long does it take your system to log you into Gnome?  From when you hit enter after typing your password to when the desktop is displayed and the mouse cursor isn't animated busy?

---

### Post by graysky on 2009-01-16
This is a known issue with Intrepid... the link below shows the solution.

[http://ubuntuforums.org/showthread.php?t=1002049](http://ubuntuforums.org/showthread.php?t=1002049)

---

