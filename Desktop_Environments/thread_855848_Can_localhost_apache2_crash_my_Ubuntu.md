---
title: "Can localhost apache2 crash my Ubuntu?"
date: 2008-07-10
forum: Desktop Environments
---

### Post by aeshanw on 2008-07-10
My PC keeps crashing periodically.i checked the logs to find:
Jul 11 09:39:01 aeshan-desktop /USR/SBIN/CRON[6302]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jul 11 09:48:04 aeshan-desktop syslogd 1.5.0#1ubuntu1: restart.


My Apache log says
[Fri Jul 11 09:48:14 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.1 with Suhosin-Patch configured -- resuming normal operations

IS it my apache2?whats Suhosin-Patch ?
Thanks

---

### Post by aeshanw on 2008-07-10
Happend again!

this time its the same error followed by some other stuff:

Jul 11 10:09:01 aeshan-desktop /USR/SBIN/CRON[6684]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jul 11 10:12:56 aeshan-desktop kernel: [ 1543.196133] NVRM: Xid (0005:00): 9, Channel 00000020 Instance 00000000 Intr 00100000
Jul 11 10:13:08 aeshan-desktop kernel: [ 1555.446557] NVRM: Xid (0005:00): 6, PE0002 0438 fff3f0ed 0000f298 00000000 fff0ece8
Jul 11 10:13:08 aeshan-desktop kernel: [ 1555.447452] NVRM: Xid (0005:00): 36,  L0 -> L0
Jul 11 10:13:08 aeshan-desktop kernel: [ 1555.478447] NVRM: Xid (0005:00): 6, PE0002 0438 fff3f0ed 00000000 00000000 00000000
Jul 11 10:13:08 aeshan-desktop kernel: [ 1555.479331] NVRM: Xid (0005:00): 36,  L0 -> L0
Jul 11 10:13:20 aeshan-desktop kernel: [ 1567.529737] NVRM: Xid (0005:00): 6, PE0002 0448 00000000 0000f310 00000000 00000000
Jul 11 10:13:20 aeshan-desktop kernel: [ 1567.530633] NVRM: Xid (0005:00): 36,  L0 -> L0
Jul 11 10:13:20 aeshan-desktop kernel: [ 1567.656434] NVRM: Xid (0005:00): 6, PE0002 0428 7da28482 0000fa38 00000000 ffede8e3
Jul 11 10:13:20 aeshan-desktop kernel: [ 1567.657329] NVRM: Xid (0005:00): 36,  L0 -> L0
Jul 11 10:13:20 aeshan-desktop kernel: [ 1567.708589] NVRM: Xid (0005:00): 6, PE0002 0438 12ededed 00000000 00000000 00efebe7

Thing is , I was able to move-my mouse around (perhaps thats the NVRM Xid stuff) , but the screen hangs after the /USR/SBIN/CRON[6684].
I switched off my apache. hope it works now.

---

### Post by aeshanw on 2008-07-10
Hmm disabled apache2 but it still crashes:

Jul 11 11:28:13 aeshan-desktop kernel: [ 1524.173438] NVRM: Xid (0005:00): 6, PE0002 1900 001703ba 0000fdbc 00000000 00020011
Jul 11 11:28:13 aeshan-desktop kernel: [ 1524.174328] NVRM: Xid (0005:00): 36,  L0 -> L0
Jul 11 11:28:13 aeshan-desktop kernel: [ 1524.190951] NVRM: Xid (0005:00): 6, PE0002 1900 001703ba 00000000 00000000 00000000
Jul 11 11:28:13 aeshan-desktop kernel: [ 1524.191833] NVRM: Xid (0005:00): 36,  L0 -> L0
Jul 11 11:28:25 aeshan-desktop kernel: [ 1536.211440] NVRM: Xid (0005:00): 6, PE0002 1910 00000018 0000fdac 00000000 00000000
Jul 11 11:28:25 aeshan-desktop kernel: [ 1536.212331] NVRM: Xid (0005:00): 36,  L0 -> L0
Jul 11 11:28:26 aeshan-desktop kernel: [ 1536.292848] NVRM: Xid (0005:00): 6, PE0002 190c 00000000 0000ee5c 00000000 00000000
Jul 11 11:28:26 aeshan-desktop kernel: [ 1536.293756] NVRM: Xid (0005:00): 36,  L0 -> L0
Jul 11 11:28:26 aeshan-desktop kernel: [ 1536.338554] NVRM: Xid (0005:00): 6, PE0002 063c 80f7f5f3 0000f8dc 00000000 00010000
Jul 11 11:28:26 aeshan-desktop kernel: [ 1536.339445] NVRM: Xid (0005:00): 36,  L0 -> L0

Whats NVRM: Xid ?

---

