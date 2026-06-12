---
title: "Issue with Compiz and  AWN."
date: 2009-04-17
forum: Desktop Environments
---

### Post by frozenhell on 2009-04-17
hi everyone, 
I am new to the forum. Been using ubuntu daily for 3 days.

I got to costumize my desktop with awn. everything run smoothly since i plugged my sony tv with my laptop. I had then to use the Screen Resolution manager (included with ubuntu). I then, changed the resolution of my TV then asked me to relog to update the changes.

I ended up by some weird resolution (like my desktop was split in two betweenn my monitor and the TV) Half of the diplay was mon my laptop monitor and the other half o the TV, but i could not see awn Bar anymore. I then restarded my computer to see if it is going to show up again. BUT no.

When i checked my syslog i found:
**Apr 17 19:00:48 Opiate kernel: [ 1378.223811] awn-manager[8673]: segfault at 20 ip b7caec61 sp bffdde90 error 4 in libgobject-2.0.so.0.1800.2[b7ca2000+3c000]**


And when I want to run it from the terminal it says:

**Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.**


Finally, when i go to appearace. The "custom" radio button is unchecked. It is set by default to "none" (which is weird because i had it on "custom before the incident". When i want to choose "custom mode"  is says "Desktop effect could not be enabled").

_Syslog:_

**[B]Apr 17 19:18:10 Opiate -- MARK --**

[B]
(EE) intel(0): Mode 1280x1024 does not fit virtual size 2640x800 - internal error[/B]

[U]
Additional syslog:[/U]

Apr 17 18:53:28 Opiate pulseaudio[7158]: module-x11-xsmp.c: X11 session manager not running.
Apr 17 18:53:28 Opiate pulseaudio[7158]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Apr 17 18:59:55 Opiate pulseaudio[8215]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 17 18:59:55 Opiate pulseaudio[8217]: pid.c: Stale PID file, overwriting.
Apr 17 18:59:55 Opiate pulseaudio[8217]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 17 18:59:55 Opiate pulseaudio[8217]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 17 18:59:55 Opiate pulseaudio[8217]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Apr 17 18:59:55 Opiate pulseaudio[8217]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Apr 17 18:59:55 Opiate pulseaudio[8217]: alsa-util.c: Cannot find fallback mixer control "Mic".
Apr 17 19:00:08 Opiate pulseaudio[8217]: module-x11-xsmp.c: X11 session manager not running.
Apr 17 19:00:08 Opiate pulseaudio[8217]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.[/B]


P.S: I guess it is more a Compiz problem because awn seems to be running as a task. It just needs compiz to work.


PLEASE HELP :)

---

### Post by frozenhell on 2009-04-17
ubutu 8.10

Last compiz
Last aw

---

### Post by frozenhell on 2009-04-17
I am sorry for bumping but i need your help guys.

I am upgrading to 9.04 hoping it is going to solve the problem.

what do you think guys ?

---

### Post by jg1395 on 2009-04-17
You need to get your intel videocard working properly with your tv.  I'm assuming 1920x1080

---

