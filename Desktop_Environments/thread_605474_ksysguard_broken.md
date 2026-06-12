---
title: "ksysguard broken"
date: 2007-11-07
forum: Desktop Environments
---

### Post by CalZing on 2007-11-07
I've had this annoying problem for a while. When i launch ksysguard, I can't get any information out of it. It seems lika ksysguard can't connect to the localhost or something similiar.  When I launch it using ctrl + esc the process list is empty and the stats at the bottom (processes, Ram, etc) i just filled with 8's (88888 processes running, etc).

Any suggestions? I can still launch a console and use ps though if I want to kill applications...

---

### Post by dabl on 2007-11-07
You have lm-sensors installed, right?  Maybe you need to run ```
sudo sensors-detect
``` again.  Then run ksysguard and see if it is picking up the sensor outputs. :)

---

### Post by CalZing on 2007-11-08
suddenly it just started working again. Don't know why, but the computer had been shut domn and now it works, and I didn't do your command or anything... strange

---

### Post by GeneralZod on 2007-11-08
> **CalZing said:**
> suddenly it just started working again. Don't know why, but the computer had been shut domn and now it works, and I didn't do your command or anything... strange

ksysguard relies on a daemon (called ksysguardd) to give it the information it needs.  This daemon is started automatically sometime during boot-up.  It's possible that the daemon crashed (which would account for your problem) and was then restarted when you rebooted (which would account for your now lack of problem :))

---

