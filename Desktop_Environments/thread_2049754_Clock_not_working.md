---
title: "Clock not working"
date: 2012-08-29
forum: Desktop Environments
---

### Post by jalone on 2012-08-29
HI all, i am using a virtual ubuntu 12.04 (parallel) with classical gnome de (no unity) and i am trying to set the OS clock.

whenever i try to set a network one or set it manually through GUI, suddenly the the minutes go some forward, and after a while or reboot both date and time are screwed of several days/hours/mins 

it really bothers me cos i am using SVN and some backup facilities whose data would be screwed by these inconsistencies.

i would like to understand if its a known problem, a virtual machine issue or maybe a solution.

Thank you.

---

### Post by chubble10 on 2012-08-29
If they are running in VMs, they usually copy the time from the host PC. Will it try to stay in sync with the host or just randomly keep shifting?

---

### Post by Lars Noodén on 2012-08-29
Do you have either ntp or openntpd installed yet?  If so, what do the logs (/var/log/syslog) say?

---

### Post by jalone on 2012-08-29
> **chubble10 said:**
> If they are running in VMs, they usually copy the time from the host PC. Will it try to stay in sync with the host or just randomly keep shifting?

the host machine clock run perfectly. i am noticing now that it shift back (almost a month) after any VM reboot. and if i try to correct it through the GUI it will not accept my values for the minutes, going ~8 minutes ahead. now its a while the machine is up and the outsync is of about 12 minutes...

it's so weird.

> Do you have either ntp or openntpd installed yet? If so, what do the logs (/var/log/syslog) say?

no, neither ntp, nor openntp :/

---

