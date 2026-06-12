---
title: "Error Evaluating GTM - on Startup..."
date: 2006-02-13
forum: Desktop Environments
---

### Post by mednamot on 2006-02-13
I didn't see an error when I shut down (when searching the forums, everything seems to be geared towards that) but I installed two games this morning (can't remember which two, one was the Warcraft-like RTS, the other I think was some kids games - for my daughter), and I shut down the laptop to take it to work, when I got on the train and started it up, it goes through all the loading, gives me the login screen for half a second, then goes all black with a flashing cursor in the top left corner.

couple minutes later, I get the error message.

my Ubuntu using coworker suggesting a complete reinstall, but I'd rather not go through that, and would instead like to learn how to fix it.

Also, I tried booting into recovery mode, but it thinks the computer is overheated (doubtful at worst, as it's been off for a good 2 hours) and restarts at the command prompt.

been running this cleanly (seemingly) since Saturday morning, would hate to have to redo it, but if I must I must.

any tips?

---

### Post by nocturn on 2006-02-13
Did it say GTM?  

You can still log in on a console (CTRL-ALT-F1), what is the output of dmesg, what are the last lines in /var/log/syslog

---

### Post by nocturn on 2006-02-13
Another question, did you shut it down or put it to sleep (suspend or hibernate)?

The GTM error seems to be ACPI related.

---

### Post by nocturn on 2006-02-13
[http://ubuntuforums.org/showthread.php?t=121880](http://ubuntuforums.org/showthread.php?t=121880)

seems related (no fix there).

I'd file it as a bug in any case (because it may reappear on reinstall).

---

### Post by mednamot on 2006-02-13
I can't get it to boot at all - if I boot to console I get the overheated error (which it's not) and then the "error evaluating _GTM" code which autoshuts down, and if I boot normally I just get the error.

I'm dl'ing a LIVE cd right now to hopefully get some form of access to the computer, the only question I have is do I log in as my user with the LIVE cd or does it set something else up?

---

### Post by mednamot on 2006-02-13
After looking up ACPI, I come to realize that makes sense as a problem, as Ubuntu does crazy stuff with my laptop battery, sometimes showing it charging when it's not plugged in, or showing it's running on battery when it is plugged in, as well as telling me (after charging all night) that my battery is about dead.

*off to do some more research while waiting for LIVE cd to finish*

---

### Post by mednamot on 2006-02-13
Bios update completely fixed it...

*dances the dance of happiness*

next task - get my 2wire card recognized

---

### Post by mednamot on 2006-03-01
yeah...so the BIOS update completely fixed it for a week...

at which point I changed by boot modules (using one of the HOWTO's) which completely hosed the computer (at least I thought that's what caused it).

I fully reinstalled (a week ago Monday) and everything was fine untill Monday afternoon (a week from install nearly exactly) when it crashed out on me and wouldn't boot.

I'm presently trying gentoo, but it doesn't even want to install for me, and I'd really rather stick with Ubuntu.

I'm probably going to re-install Ubuntu tonight, but I'm concerned that next Wednesday/Thursday I'll be doing it all over again...

any way to disable ACPI?

---

