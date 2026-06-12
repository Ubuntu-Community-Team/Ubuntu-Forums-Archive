---
title: "How to schedule tasks in Kcron so that they get started at every pc startup ?"
date: 2007-04-03
forum: Desktop Environments
---

### Post by samir85 on 2007-04-03
Could anybody help me at this?

regards Samir

---

### Post by H3g3m0n on 2007-04-03
This isn't really a job for cron, its designed to run tasks at specific times not on system events.

You could in theory write a script that refuses to execute after its been run one, such as by checking to see if something is already running and then set cron to run that script continuously my setting all fields to * but this isn't really a good way to do it.

The easiest way is probably to edit /etc/rc.local and add the commands you want run at boot.

You can also make a script in /etc/init.d/ with the commands you want executed at diffrent run level events such as start and stop etc..., then you need to make a link to it in the correct runlevel /etc/rc#.d/ with the same file naming scheme that is there. Stuff in /etc/rc.local is executed by the script /etc/init.d/rc.local when entering runlevels.

Theres more indepth info here:
[http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit](http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit)

---

### Post by MontanaMax on 2007-04-03
You can also create a symbolic link in ~/.kde/Autostart to the scripts if they need to be run at user login (which is different than PC startup, but might meet your need).

---

### Post by pppetter on 2007-04-03
Please note that if you really want it to start at the real startup(before kde and everything is started) with rc.local use > su -username
at the start of the command, where username is your username or else it will run as root.

---

