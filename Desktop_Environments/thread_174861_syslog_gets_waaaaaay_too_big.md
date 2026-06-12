---
title: "syslog gets waaaaaay too big"
date: 2006-05-12
forum: Desktop Environments
---

### Post by linuxgrrl on 2006-05-12
hi,
I set up a Ubuntu MythTv box for my parents and they love it.  There is only one problem: every two months or so, gdm will not start because the ubuntu partition is full.   The culprit is the syslog and kern.log files which get HUGE (I'm talking several GB).  It's a real pain to fix because the ubuntu gdm "boot to terminal" option doesn't work  (it never has in my experience), and I have to haul in a wired keyboard from my house to interrupt the boot sequence and perform surgery.

Is there some way to stop these logs from getting so big, or perhaps force them to be automatically deleted whenever the machine is rebooted?  

thanks,
Mary

---

### Post by cyracks on 2006-05-12
Configuration file for setting log rotation/deletion is
/etc/logrotate.conf

---

### Post by linuxgrrl on 2006-05-17
thanks.  I looked at the config file, and everywhere that it said "monthly," I changed to "daily".  Hopefully that does it.  I'm still scratching my head tho' ... if the logs were rotating monthly, why would they choke every 2.5 months or so?   

Guess I'll see what happens...

---

### Post by cyracks on 2006-05-17
[QUOTE=linuxgrrl]... if the logs were rotating monthly, why would they choke every 2.5 months or so?   
[/QUOTE]

# see **"man logrotate"** for details

# keep 4 weeks worth of backlogs
**rotate** 4

---

