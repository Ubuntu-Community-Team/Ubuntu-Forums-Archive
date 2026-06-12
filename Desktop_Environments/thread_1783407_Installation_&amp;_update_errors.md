---
title: "Installation &amp; update errors"
date: 2011-06-15
forum: Desktop Environments
---

### Post by 9a8sy on 2011-06-15
Whenever I do an update or even install new software, I keep getting update errors. However it appears the updates did load because if I go back it shows they no longer need to be updated. The error log is very log and doesn't really tell me anything helpful. Where would I find how to correct this issue?

---

### Post by ivanovnegro on 2011-06-15
It would not be bad to see here the error log, if you want serious help.
You could also post here your sources list with that command:

```
sudo cat /etc/apt/sources.list
```

or look in the Software Center/Synaptic for added/other software.

---

### Post by 9a8sy on 2011-06-15
Here it be:
dharden@dennis-laptop:~$ sudo cat /etc/apt/sources.list
[sudo] password for dharden: 
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
# deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main #Third party developers repository

---

### Post by kronick on 2011-06-15
the error log?

---

### Post by 9a8sy on 2011-06-15
Is that in the syslog1? I'm trying to send it but it keeps failing on here. Maybe it's too big for this forum

---

### Post by 9a8sy on 2011-06-15
Here is part of syslog1:I think this is what you need:

 dennis-laptop CRON[17901]: (root) CMD ([ -x /usr/share/gforge/bin/install-ftp.sh ] && /usr/share/gforge/bin/install-ftp.sh update > /dev/null 2>&1)
Jun 15 00:00:01 dennis-laptop CRON[17902]: (root) CMD ([ -x /usr/share/gforge/bin/ftp_create_group_access.php ] && /usr/bin/php5 -d include_path=$INCLUDE_PATH /usr/share/gforge/bin/ftp_create_group_access.php > /dev/null 2>&1)
Jun 15 00:00:01 dennis-laptop CRON[17896]: (CRON) error (grandchild #17902 failed with exit status 1)
Jun 15 00:00:01 dennis-laptop CRON[17907]: (root) CMD ([ -x /usr/share/gforge/bin/update-user-group-ssh.sh ] && /usr/share/gforge/bin/update-user-group-ssh.sh > /dev/null 2>&1)
Jun 15 00:00:01 dennis-laptop CRON[17908]: (root) CMD ($PHP $FFCRON/create_scm_repos.php)
Jun 15 00:00:01 dennis-laptop CRON[17916]: (gforge) CMD ($PHP $FFCRON/rotate_activity.php)
Jun 15 00:00:01 dennis-laptop CRON[17898]: (CRON) error (grandchild #17908 failed with exit status 255)
Jun 15 00:00:01 dennis-laptop CRON[17899]: (CRON) error (grandchild #17916 failed with exit status 255)
Jun 15 00:00:02 dennis-laptop CRON[17900]: (CRON) error (grandchild #17907 failed with exit status 255)
Jun 15 00:00:33 dennis-laptop kernel: [27411.272905] [UFW BLOCK] IN=wlan1 OUT= MAC=00:0f:66:3c:39:ee:00:0f:66:ad:72:cb:08:00 SRC=66.220.145.38 DST=192.168.1.106 LEN=441 TOS=0x00 PREC=0x00 TTL=233 ID=55824 DF PROTO=TCP SPT=443 DPT=56311 WINDOW=60 RES=0x00 ACK PSH URGP=0 
Jun 15 00:01:46 dennis-laptop kernel: [27484.646555] [UFW BLOCK] IN=wlan1 OUT= MAC=01:00:5e:00:00:fb:f4:ce:46:08:7f:a0:08:00 SRC=192.168.1.114 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=45822 PROTO=2 
Jun 15 00:01:48 dennis-laptop kernel: [27486.488368] [UFW BLOCK] IN=wlan1 OUT= MAC=01:00:5e:00:00:01:00:14:bf:cb:b1:67:08:00 SRC=192.168.3.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=19 PROTO=2 
Jun 15 00:01:50 dennis-laptop kernel: [27489.071678] [UFW BLOCK] IN=wlan1 OUT= MAC=01:00:5e:00:00:fb:f4:ce:46:08:7f:a0:08:00 SRC=192.168.1.114 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=46018 PROTO=2 
Jun 15 00:03:46 dennis-laptop kernel: [27604.453730] [UFW BLOCK] IN=wlan1 OUT= MAC=01:00:5e:00:00:01:00:0f:66:ad:72:cb:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
Jun 15 00:03:50 dennis-laptop kernel: [27608.754656] [UFW BLOCK] IN=wlan1 OUT= MAC=01:00:5e:00:00:fb:f4:ce:46:08:7f:a0:08:00 SRC=192.168.1.114 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=47596 PROTO=2 
Jun 15 00:04:51 dennis-laptop kernel: [27669.526720] [UFW BLOCK] IN=wlan1 OUT= MAC=00:0f:66:3c:39:ee:00:0f:66:ad:72:cb:08:00 SRC=66.220.145.38 DST=192.168.1.106 LEN=297 TOS=0x00 PREC=0x00 TTL=233 ID=41879 DF PROTO=TCP SPT=443 DPT=46216 WINDOW=61 RES=0x00 ACK PSH URGP=0 
Jun 15 00:05:12 dennis-laptop kernel: [27690.904353] [UFW BLOCK] IN=wlan1 OUT= MAC=00:0f:66:3c:39:ee:00:0f:66:ad:72:cb:08:00 SRC=66.220.145.38 DST=192.168.1.106 LEN=297 TOS=0x00 PREC=0x00 TTL=233 ID=41880 DF PROTO=TCP SPT=443 DPT=46216 WINDOW=61 RES=0x00 ACK PSH URGP=0 
Jun 15 00:05:52 dennis-laptop kernel: [27730.611207] [UFW BLOCK] IN=wlan1 OUT= MAC=01:00:5e:00:00:01:00:0f:66:ad:72:cb:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
Jun 15 00:05:53 dennis-laptop kernel: [27731.328218] [UFW BLOCK] IN=wlan1 OUT= MAC=01:00:5e:00:00:fb:f4:ce:46:08:7f:a0:08:00 SRC=192.168.1.114 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=47667 PROTO=2 
Jun 15 00:05:55 dennis-laptop kernel: [27733.660203] [UFW BLOCK] IN=wlan1 OUT= MAC=00:0f:66:3c:39:ee:00:0f:66:ad:72:cb:08:00 SRC=66.220.145.38 DST=192.168.1.106 LEN=297 TOS=0x00 PREC=0x00 TTL=233 ID=41881 DF PROTO=TCP SPT=443 DPT=46216 WINDOW=61 RES=0x00 ACK PSH URGP=0 
Jun 15 00:06:08 dennis-laptop kernel: [27746.483528] [UFW BLOCK] IN=wlan1 OUT= MAC=01:00:5e:00:00:01:00:14:bf:cb:b1:67:08:00 SRC=192.168.3.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=29 PROTO=2 
Jun 15 00:06:10 dennis-laptop kernel: [27749.248274] [UFW BLOCK] IN=wlan1 OUT= MAC=01:00:5e:00:00:fb:f4:ce:46:08:7f:a0:08:00 SRC=192.168.1.114 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=48648 PROTO=2 
Jun 15 00:07:58 dennis-laptop kernel: [27856.666246] [UFW BLOCK] IN=wlan1 OUT= MAC=01:00:5e:00:00:01:00:0f:66:ad:72:cb:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
Jun 15 00:08:05 dennis-laptop kernel: [27863.629757] [UFW BLOCK] IN=wlan1 OUT= MAC=01:00:5e:00:00:fb:f4:ce:46:08:7f:a0:08:00 SRC=192.168.1.114 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=49812 PROTO=2 
Jun 15 00:09:01 dennis-laptop CRON[18121]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)

---

### Post by ivanovnegro on 2011-06-15
The sources list seems ok, but what error did you have while updating the system?

---

### Post by 9a8sy on 2011-06-15
It was a long log file that shows up every time I do an update. Where can I go to retrieve that info? Otherwise I'll copy it tomorrow or whenever some update is released again.

---

### Post by ivanovnegro on 2011-06-15
Ok, try to update now your system and while doing this, click on the "+" sign, I think it is this, to have additional info what is going on in the meantime, when it stops, just copy with the right click the output, should work I think.
Also what is the update manager saying when it stops if it stops.

---

### Post by 9a8sy on 2011-06-15
Hitting the + sign didn't do anything. I says there are no updates at this time. If I remember correctly, it just says there were errors. You can view them in a little window and there seems to be a lot of info in it. After I click OK or whatever, it seems as if everything is finished. If I try to go back and check for updates, there are none.

OK, I just tried to install a new piece of software. I got the error that says Package Operation Failed The log is as follows:

nstallArchives() failed: Selecting previously deselected package convertall.

(Reading database ... 
(Readiing database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 335207 files and directories currently installed.)

Unpacking convertall (from .../convertall_0.4.2-1_all.deb) ...

Processing triggers for bamfdaemon ...

Rebuilding /usr/share/applications/bamf.index...

Processing triggers for desktop-file-utils ...

Processing triggers for python-gmenu ...

Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache...

Processing triggers for menu ...

Processing triggers for python-support ...

Setting up gforge-db-postgresql (5.0.2-5) ...

Calculating defaults

Reading defaults from /etc/fusionforge/fusionforge.conf

Creating /etc/fusionforge/fusionforge.conf

SSL Disabled

Creating /etc/gforge/httpd.conf

Creating /etc/gforge/httpd.secrets

Creating /etc/gforge/local.inc

Creating other includes

 * Reloading PostgreSQL 8.3 database server

   ...done.

Procedural language on fusionforge already enabled

You'll see some debugging info during this installation.

Do not worry unless told otherwise.

DBI connect('dbname=fusionforge','fusionforge',...) failed: FATAL:  Ident authentication failed for user "fusionforge" at /usr/share/gforge/lib/include.pl line 35

Uncaught exception from user code:

	Error while connecting to database:  at /usr/share/gforge/lib/include.pl line 37.

 at /usr/share/gforge/lib/include.pl line 37

	main::db_connect called at /usr/share/gforge/bin/db-upgrade.pl line 36

dpkg: error processing gforge-db-postgresql (--configure):

 subprocess installed post-installation script returned error exit status 255

No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of gforge-shell-postgresql:

 gforge-shell-postgresql depends on gforge-db-postgresql; however:

  Package gforge-db-postgresql is not configured yet.

dpkg: error processing gforge-shell-postgresql (--configure):

 dependency problems - leaving unconfigured

No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of gforge-ftp-proftpd:

 gforge-ftp-proftpd depends on gforge-shell-postgresql | gforge-shell; however:

  Package gforge-shell-postgresql is not configured yet.

  Package gforge-shell is not installed.

  Package gforge-shell-postgresql which provides gforge-shell is not configured yet.

dpkg: error processing gforge-ftp-proftpd (--configure):

 dependency problems - leaving unconfigured

No apport report written because MaxReports is reached already
Setting up convertall (0.4.2-1) ...

Processing triggers for menu ...

Errors were encountered while processing:

 gforge-db-postgresql

 gforge-shell-postgresql

 gforge-ftp-proftpd

Setting up gforge-db-postgresql (5.0.2-5) ...

Calculating defaults

Reading defaults from /etc/fusionforge/fusionforge.conf

Creating /etc/fusionforge/fusionforge.conf

SSL Disabled

Creating /etc/gforge/httpd.conf

Creating /etc/gforge/httpd.secrets

Creating /etc/gforge/local.inc

Creating other includes

 * Reloading PostgreSQL 8.3 database server

   ...done.

Procedural language on fusionforge already enabled

You'll see some debugging info during this installation.

Do not worry unless told otherwise.

DBI connect('dbname=fusionforge','fusionforge',...) failed: FATAL:  Ident authentication failed for user "fusionforge" at /usr/share/gforge/lib/include.pl line 35

Uncaught exception from user code:

	Error while connecting to database:  at /usr/share/gforge/lib/include.pl line 37.

 at /usr/share/gforge/lib/include.pl line 37

	main::db_connect called at /usr/share/gforge/bin/db-upgrade.pl line 36

dpkg: error processing gforge-db-postgresql (--configure):

 subprocess installed post-installation script returned error exit status 255

dpkg: dependency problems prevent configuration of gforge-shell-postgresql:

 gforge-shell-postgresql depends on gforge-db-postgresql; however:

  Package gforge-db-postgresql is not configured yet.

dpkg: error processing gforge-shell-postgresql (--configure):

 dependency problems - leaving unconfigured

dpkg: dependency problems prevent configuration of gforge-ftp-proftpd:

 gforge-ftp-proftpd depends on gforge-shell-postgresql | gforge-shell; however:

  Package gforge-shell-postgresql is not configured yet.

  Package gforge-shell is not installed.

  Package gforge-shell-postgresql which provides gforge-shell is not configured yet.

dpkg: error processing gforge-ftp-proftpd (--configure):

 dependency problems - leaving unconfigured

---

### Post by ivanovnegro on 2011-06-15
Ok, the program GForge seems the culprit, how did you install the program? Was it a deb file or from the Software Center?

---

### Post by 9a8sy on 2011-06-15
I'm not sure. I don't even know what the program is. I couldn't find it to run so I did a google search but from what I read, it doesn't ring a bell as to why I would have even have installed it.

---

### Post by ivanovnegro on 2011-06-15
Ok, but do you have the program actually installed or did I saw something that does even not exist on your machine?. :confused: Look for it in the Software Center/Synaptic by typing its name, if it is installed and you dont need it, remove it.

---

### Post by 9a8sy on 2011-06-15
Excellent!! I found it that way and removed it. I then checked and it found an update which installed with no problems!! I think I'm good to go now. Thanks!!!

---

