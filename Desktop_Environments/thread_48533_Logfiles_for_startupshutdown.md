---
title: "Logfiles for startup/shutdown?"
date: 2005-07-12
forum: Desktop Environments
---

### Post by Vortacist on 2005-07-12
So, when you start up or shut down Ubuntu, you see a lot of nice, relatively human-readable messages like:

Someservice-or-other starting.....................[ok]

I'm trying to troubleshoot a problem right now, and I would really like to see what's going on at startup/shutdown.  /var/log/messages does not seem to have much info about what's going on; here, for example, is all that you see when my computer reboots:

Jul 12 09:35:19 localhost exiting on signal 15
Jul 12 10:10:39 localhost syslogd 1.4.1#16ubuntu6: restart.

That was it, my system restarted between those two lines.  Watching the monitor during the shutdown, tons of potentially useful information was scrolling by.  Unfortunately, it's too fast for me to read or write down for later use.

Is all of this nice stuff that's being output to the screen logged somewhere?  If so, where can I find it?  If not, is there some way that I can start logging it?

Thanks for your help!

---

### Post by Xian on 2005-07-12
Try using Shift+PgUp/Shift+PgDn to view messages which have scrolled beyond the screen. Or perhaps Control-S during startup to pause the display of messages scrolling past. Control-Q resumes.

And let us know if it works. :)

There is no boot log, save that you might want to modify the scripts in /etc/init.d/ to execute logger for each time that output is displayed. Have fun with that little task.

---

### Post by Vortacist on 2005-07-15
[QUOTE=Xian]Or perhaps Control-S during startup to pause the display of messages scrolling past. Control-Q resumes.
[/QUOTE]

Control-S and Control-Q worked beautifully.  That was just what I needed - thanks very much! :)

---

