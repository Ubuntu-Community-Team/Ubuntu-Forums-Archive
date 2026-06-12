---
title: "Ubuntu 9.04 System Crash"
date: 2009-06-03
forum: General Help
---

### Post by modjoa on 2009-06-03
Hi Guys,
Today I update my computer with Ubuntu 9.04 and a BIG problem comes:
The system begin to reboot randomly, when I start browsing the web...
Initially, I was thinking that it is caused by the Nvidia Drivers, so I switch them off, but this does not solve the problem. 
The **/var/log/syslog** contains the following information, during the time when the system has been rebooted:

[I][B]Jun 3 20:17:01 /USR/SBIN/CRON[3466]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 3 20:20:01 /USR/SBIN/CRON[3550]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jun  3 20:22:00 syslogd 1.5.0#5ubuntu3: restart.[/B][/I]

Any clues what might be the reason?
How can I get more detailed information about the system crash?

---

### Post by utnubuuser on 2009-06-03
Hi  -- have you tried:> sudo dpkg --configure -a(This might not work in Jaunty anymore, but it's worth a shot).

You could also go to synaptic and use the filters to look for broken packages.

---

### Post by modjoa on 2009-06-04
Thanks for the reply.
I have checked - there is no broken packages.

---

### Post by rax_m on 2009-06-04
Sometimes when systems reboot randomly it can be caused by overheating. 
Do you know what your CPU and GPU temperatures are getting up to? 
Is it a desktop or a laptop?

---

### Post by modjoa on 2009-06-04
I am using it on a Desktop - I have open the case and I have checked the fans - there is no problem with them. In BIOS, the temperatures seem to be normal.
The system runs normally without any problems under M$ Windows XP...

---

### Post by modjoa on 2009-06-05
Today, I got a similar problem on my notebook- HP 6720S (the system just stalled), which is running successfully Ubuntu 9.04 for over 2 months without any problems.
The msg of the error is as follows:

> Jun  5 14:40:01 /USR/SBIN/CRON[4421]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jun  5 14:50:01  /USR/SBIN/CRON[4844]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jun  5 15:00:02  /USR/SBIN/CRON[5174]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Jun  5 15:00:02  /USR/SBIN/CRON[5196]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jun  5 15:10:01  /USR/SBIN/CRON[5573]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)

---

