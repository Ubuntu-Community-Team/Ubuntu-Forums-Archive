---
title: "Warning: /sbin/init INFECTED"
date: 2017-08-01
forum: Fedora/RedHat and derivatives
---

### Post by yohanankap on 2017-08-01
Hello,
a few days ago I install on my centos 7 that run with WHM software the ConfigServer Server Services.
I got a report that warning about some infection:
find: ‘/proc/32494’: No such file or directory


/usr/lib/debug/usr/.dwz


Warning: /sbin/init INFECTED
INFECTED (PORTS: 465)
You have 2 process hidden for readdir command
You have 2 process hidden for ps command
chkproc: Warning: Possible LKM Trojan installed
eno16777728: PF_PACKET(/usr/sbin/dhclient)
The tty of the following user process(es) were not found
in /var/run/utmp !
! RUID PID TTY CMD
! -Dsolr.autoSoftCommit.maxTime=30-Dsolr.log.muteconsole -XX:OnOutOfMemoryError=/home/cpanelsolr/bin/oom_solr.sh 8984 /home/cpanelsolr/server/logs -jar start.jar --module=http
0 olr.install.dir=/home/cpanelsolr-Dsolr.autoSoftCommit.maxTime=30-Dsolr.log.muteconsole -XX:OnOutOfMemoryError=/home/cpanelsolr/bin/oom_solr.sh 8984 /home/cpanelsolr/server/logs -jar start.jar --module=http
-Dsolr.log.muteconsole -XX:OnOutOfMemoryError=/home/cpanelsolr/bin/oom_solr.sh 8984 /home/cpanelsolr/server/logs -jar start.jar --module=http

How do I need to act with this report?
Thank you.

---

### Post by TheFu on 2017-08-01
Don't know.  Perhaps tell the centos people?
These are Ubuntu forums.

---

### Post by yohanankap on 2017-08-01
Thank you!

---

### Post by TheFu on 2017-08-01
I don't use CentOS or cpanel or know what WHM is.  Sounds like something a VPS provider uses.  If I saw that error on one of my VPS systems, I'd wipe it and start over from a known-good source and NOT load any 3rd party tools, then run the scan.

BTW, lots of the warnings from scanners put out false positives. That has been an issue for 20 yrs.

I did a web search on the exact warning and found lots and lots of people looking for help and lots of "experts" saying it was a false positive - sometimes on freshly installed systems!

If you are positive of the history for the system and know it couldn't have been compromised and **all** the added software came from trustworthy sources, then I wouldn't worry and would update the signatures for the new init files.
If I wasn't - I'd shoot the VPS in the head and start over.  That's kinda the point of VPS systems.

---

