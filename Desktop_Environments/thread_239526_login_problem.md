---
title: "login problem"
date: 2006-08-19
forum: Desktop Environments
---

### Post by abhiomkar on 2006-08-19
I tried to install aiglx on my system, i fallowed [http://www.ubuntuforums.org/showthread.php?t=145068](http://www.ubuntuforums.org/showthread.php?t=145068) to install it...
i added below repos & did apt-get update , apt-get dist-upgrade
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper aiglx
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

(lspci output > [http://paste.ubuntu-nl.org/d20889](http://paste.ubuntu-nl.org/d20889))
then i rebooted my system...
when i enter my username & password at gdm , after 2 or 3 seconds its comming back to gdm.
not able to login (except Fail Safe Terminal, Iam able to login as root, when i change(in root account) my screenresolution from 1024X768 to 800X600 X server terminates & comes to gdm)

Any Suggestions ???

.xsession-errors > [http://paste.ubuntu-nl.org/d20974](http://paste.ubuntu-nl.org/d20974)
.gdm.conf        > [http://rafb.net/paste/results/GCMNHV65.html](http://rafb.net/paste/results/GCMNHV65.html)
.xorg.conf       > [http://rafb.net/paste/results/dqF6LY47.html](http://rafb.net/paste/results/dqF6LY47.html)

Syslog at the time of login : 
Aug 18 18:29:33 localhost gdm[11138]: failsafe dialog failed (inhibitions: 0 0)
Aug 18 18:29:45 localhost gdm[11138]: failsafe dialog failed (inhibitions: 0 1)
Aug 18 18:29:57 localhost gdm[11138]: failsafe dialog failed (inhibitions: 1 1)

---

