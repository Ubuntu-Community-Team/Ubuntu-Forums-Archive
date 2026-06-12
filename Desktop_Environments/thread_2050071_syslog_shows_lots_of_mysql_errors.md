---
title: "syslog shows lots of mysql errors"
date: 2012-08-30
forum: Desktop Environments
---

### Post by clickwir on 2012-08-30
Was looking in /var/log/syslog for other things and noticed a ton of these entries. I don't know that I'm even using anything that uses mysql, I probably am and don't know it. Kubuntu 12.04 64bit.

```
Aug 30 00:50:56 hostname kernel: [1472659.694340] init: mysql main process ended, respawning
Aug 30 00:51:24 hostname kernel: [1472688.091507] init: mysql post-start process (21493) terminated with status 1
Aug 30 00:51:24 hostname kernel: [1472688.107026] type=1400 audit(1346302284.621:97921): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=21576 comm="apparmor_parser"
Aug 30 00:51:25 hostname kernel: [1472689.282794] type=1400 audit(1346302285.797:97922): apparmor="DENIED" operation="mknod" parent=1 profile="/usr/sbin/mysqld" name="/run/mysqld/mysqld.sock" pid=21580 comm="mysqld" requested_mask="c" denied_mask="c" fsuid=116 ouid=116
Aug 30 00:51:26 hostname kernel: [1472689.769021] init: mysql main process (21580) terminated with status 1
Aug 30 00:51:26 hostname kernel: [1472689.769072] init: mysql main process ended, respawning
Aug 30 00:51:54 hostname kernel: [1472718.182382] init: mysql post-start process (21581) terminated with status 1
Aug 30 00:51:54 hostname kernel: [1472718.194102] type=1400 audit(1346302314.709:97923): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=21672 comm="apparmor_parser"
Aug 30 00:51:55 hostname kernel: [1472719.375651] type=1400 audit(1346302315.889:97924): apparmor="DENIED" operation="mknod" parent=1 profile="/usr/sbin/mysqld" name="/run/mysqld/mysqld.sock" pid=21676 comm="mysqld" requested_mask="c" denied_mask="c" fsuid=116 ouid=116
Aug 30 00:51:56 hostname kernel: [1472719.766444] init: mysql main process (21676) terminated with status 1
Aug 30 00:51:56 hostname kernel: [1472719.766465] init: mysql main process ended, respawning
Aug 30 00:52:24 hostname kernel: [1472748.264704] init: mysql post-start process (21677) terminated with status 1
Aug 30 00:52:24 hostname kernel: [1472748.280607] type=1400 audit(1346302344.797:97925): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=21761 comm="apparmor_parser"
Aug 30 00:52:25 hostname kernel: [1472749.457492] type=1400 audit(1346302345.977:97926): apparmor="DENIED" operation="mknod" parent=1 profile="/usr/sbin/mysqld" name="/run/mysqld/mysqld.sock" pid=21765 comm="mysqld" requested_mask="c" denied_mask="c" fsuid=116 ouid=116
Aug 30 00:52:26 hostname kernel: [1472749.940182] init: mysql main process (21765) terminated with status 1
Aug 30 00:52:26 hostname kernel: [1472749.940233] init: mysql main process ended, respawning
Aug 30 00:52:54 hostname kernel: [1472778.357331] init: mysql post-start process (21766) terminated with status 1
Aug 30 00:52:54 hostname kernel: [1472778.372905] type=1400 audit(1346302374.889:97927): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=21850 comm="apparmor_parser"
Aug 30 00:52:56 hostname kernel: [1472779.557745] type=1400 audit(1346302376.077:97928): apparmor="DENIED" operation="mknod" parent=1 profile="/usr/sbin/mysqld" name="/run/mysqld/mysqld.sock" pid=21854 comm="mysqld" requested_mask="c" denied_mask="c" fsuid=116 ouid=116
Aug 30 00:52:56 hostname kernel: [1472780.045984] init: mysql main process (21854) terminated with status 1
Aug 30 00:52:56 hostname kernel: [1472780.046036] init: mysql main process ended, respawning
Aug 30 00:53:24 hostname kernel: [1472808.443929] init: mysql post-start process (21855) terminated with status 1
Aug 30 00:53:24 hostname kernel: [1472808.459428] type=1400 audit(1346302404.973:97929): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=21940 comm="apparmor_parser"
Aug 30 00:53:26 hostname kernel: [1472809.623058] type=1400 audit(1346302406.141:97930): apparmor="DENIED" operation="mknod" parent=1 profile="/usr/sbin/mysqld" name="/run/mysqld/mysqld.sock" pid=21944 comm="mysqld" requested_mask="c" denied_mask="c" fsuid=116 ouid=116
Aug 30 00:53:26 hostname kernel: [1472810.093229] init: mysql main process (21944) terminated with status 1
Aug 30 00:53:26 hostname kernel: [1472810.093280] init: mysql main process ended, respawning
Aug 30 00:53:55 hostname kernel: [1472838.535762] init: mysql post-start process (21945) terminated with status 1
Aug 30 00:53:55 hostname kernel: [1472838.551229] type=1400 audit(1346302435.065:97931): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=22029 comm="apparmor_parser"
Aug 30 00:53:56 hostname kernel: [1472839.819691] type=1400 audit(1346302436.337:97932): apparmor="DENIED" operation="mknod" parent=1 profile="/usr/sbin/mysqld" name="/run/mysqld/mysqld.sock" pid=22033 comm="mysqld" requested_mask="c" denied_mask="c" fsuid=116 ouid=116
Aug 30 00:53:56 hostname kernel: [1472840.318565] init: mysql main process (22033) terminated with status 1
Aug 30 00:53:56 hostname kernel: [1472840.318616] init: mysql main process ended, respawning
Aug 30 00:54:25 hostname kernel: [1472868.628858] init: mysql post-start process (22034) terminated with status 1
Aug 30 00:54:25 hostname kernel: [1472868.644351] type=1400 audit(1346302465.161:97933): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=22118 comm="apparmor_parser"
Aug 30 00:54:26 hostname kernel: [1472869.830723] type=1400 audit(1346302466.345:97934): apparmor="DENIED" operation="mknod" parent=1 profile="/usr/sbin/mysqld" name="/run/mysqld/mysqld.sock" pid=22122 comm="mysqld" requested_mask="c" denied_mask="c" fsuid=116 ouid=116
Aug 30 00:54:26 hostname kernel: [1472870.311781] init: mysql main process (22122) terminated with status 1
Aug 30 00:54:26 hostname kernel: [1472870.311838] init: mysql main process ended, respawning
Aug 30 00:54:55 hostname kernel: [1472898.720772] init: mysql post-start process (22123) terminated with status 1
Aug 30 00:54:55 hostname kernel: [1472898.736218] type=1400 audit(1346302495.253:97935): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=22206 comm="apparmor_parser"
Aug 30 00:54:56 hostname kernel: [1472899.916516] type=1400 audit(1346302496.433:97936): apparmor="DENIED" operation="mknod" parent=1 profile="/usr/sbin/mysqld" name="/run/mysqld/mysqld.sock" pid=22210 comm="mysqld" requested_mask="c" denied_mask="c" fsuid=116 ouid=116
Aug 30 00:54:56 hostname kernel: [1472900.287561] init: mysql main process (22210) terminated with status 1
Aug 30 00:54:56 hostname kernel: [1472900.287581] init: mysql main process ended, respawning
Aug 30 00:55:25 hostname kernel: [1472928.812267] init: mysql post-start process (22211) terminated with status 1
Aug 30 00:55:25 hostname kernel: [1472928.828130] type=1400 audit(1346302525.345:97937): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=22295 comm="apparmor_parser"
Aug 30 00:55:26 hostname kernel: [1472930.009847] type=1400 audit(1346302526.525:97938): apparmor="DENIED" operation="mknod" parent=1 profile="/usr/sbin/mysqld" name="/run/mysqld/mysqld.sock" pid=22299 comm="mysqld" requested_mask="c" denied_mask="c" fsuid=116 ouid=116
Aug 30 00:55:27 hostname kernel: [1472930.504609] init: mysql main process (22299) terminated with status 1
Aug 30 00:55:27 hostname kernel: [1472930.504660] init: mysql main process ended, respawning
Aug 30 00:55:55 hostname kernel: [1472958.906003] init: mysql post-start process (22300) terminated with status 1
Aug 30 00:55:55 hostname kernel: [1472958.921316] type=1400 audit(1346302555.437:97939): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=22383 comm="apparmor_parser"
Aug 30 00:55:56 hostname kernel: [1472960.104838] type=1400 audit(1346302556.621:97940): apparmor="DENIED" operation="mknod" parent=1 profile="/usr/sbin/mysqld" name="/run/mysqld/mysqld.sock" pid=22387 comm="mysqld" requested_mask="c" denied_mask="c" fsuid=116 ouid=116
Aug 30 00:55:57 hostname kernel: [1472960.608407] init: mysql main process (22387) terminated with status 1
Aug 30 00:55:57 hostname kernel: [1472960.608462] init: mysql main process ended, respawning
Aug 30 00:56:25 hostname kernel: [1472988.997113] init: mysql post-start process (22388) terminated with status 1
Aug 30 00:56:25 hostname kernel: [1472989.012711] type=1400 audit(1346302585.529:97941): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=22530 comm="apparmor_parser"
Aug 30 00:56:26 hostname kernel: [1472990.183312] type=1400 audit(1346302586.697:97942): apparmor="DENIED" operation="mknod" parent=1 profile="/usr/sbin/mysqld" name="/run/mysqld/mysqld.sock" pid=22534 comm="mysqld" requested_mask="c" denied_mask="c" fsuid=116 ouid=116
Aug 30 00:56:27 hostname kernel: [1472990.682877] init: mysql main process (22534) terminated with status 1
Aug 30 00:56:27 hostname kernel: [1472990.682929] init: mysql main process ended, respawning
Aug 30 00:56:55 hostname kernel: [1473019.090334] init: mysql post-start process (22535) terminated with status 1
Aug 30 00:56:55 hostname kernel: [1473019.105775] type=1400 audit(1346302615.621:97943): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=22619 comm="apparmor_parser"
Aug 30 00:56:56 hostname kernel: [1473020.277821] type=1400 audit(1346302616.793:97944): apparmor="DENIED" operation="mknod" parent=1 profile="/usr/sbin/mysqld" name="/run/mysqld/mysqld.sock" pid=22623 comm="mysqld" requested_mask="c" denied_mask="c" fsuid=116 ouid=116
Aug 30 00:56:57 hostname kernel: [1473020.778320] init: mysql main process (22623) terminated with status 1
Aug 30 00:56:57 hostname kernel: [1473020.778373] init: mysql main process ended, respawning

```

---

### Post by clickwir on 2012-08-30
I'm trying what's listed here: [http://tanghus.net/2012/03/yet-another-mysql-vs-apparmor-barf/](http://tanghus.net/2012/03/yet-another-mysql-vs-apparmor-barf/)

I'll report how it works.

:popcorn:

---

