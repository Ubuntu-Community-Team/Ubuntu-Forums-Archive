---
title: "applications taking a long time to load"
date: 2008-02-18
forum: Desktop Environments
---

### Post by GameboyHippo on 2008-02-18
My system recently started acting funny.  When I try to load certain applications such as firefox or mythtv, it takes a very long time to load.  Once they are loaded, they are responsive and don't present a problem.  Other applications load up quick such as gnome-terminal.  Console apps also load up fast.

I'm trying to figure out what I did to my system.  I recently had a hardware error that I thought was a software error.  So I reinstalled X.  What's interesting is that the applications that take a long time to load up simply don't do anything for awhile.  If I type in top, it just sits there.

Any clues?

---

### Post by SoDanishWasLike on 2008-03-31
I am having the problem.... any ideas?

---

### Post by Sencor on 2008-03-31
could it be some network timeouts, recently my laptop have been starting to act funny like this, it takes forever to load the gnome desktop when I login,and then some applications take forever to load while others not....and this only happens when it isn't connected to any networks, in my case I think there is something triggering the dhcp client to try to acquire a new ip address, but why doesn't the system see that I have no cable attached?   

Well maybe I'm all wrong...only some thoughts...any ideas?

---

### Post by SoDanishWasLike on 2008-04-01
This happens to me when I connected to my router and have an IP address so I don't think we have the same problem

---

### Post by roelpeeters on 2008-04-01
Did you check the logs? Are there any errors in your log files, or are there timeouts? What you can do is a 

```

ls -latr /var/log 

```

to see what log files have been modified last.

HTH

---

### Post by SoDanishWasLike on 2008-04-01
Okay I did that, but I am not sure exactly what to look for here, so I have pasted the entire output. Thanks =)

```
danish@danish-laptop:~$ ls -latr /var/log
total 4428
drwxr-xr-x  2 root   root   4096 2007-10-01 05:21 unattended-upgrades
drwxr-xr-x  2 root   root   4096 2007-10-12 13:21 dist-upgrade
drwxr-xr-x  2 root   root   4096 2007-10-14 02:49 apparmor
drwxr-xr-x  2 root   root   4096 2007-10-15 16:17 fsck
-rw-r-----  1 root   adm      31 2007-10-15 16:17 boot
-rw-r-----  1 syslog adm       0 2007-10-15 16:18 mail.warn
-rw-r-----  1 syslog adm       0 2007-10-15 16:18 mail.log
-rw-r-----  1 syslog adm       0 2007-10-15 16:18 mail.info
-rw-r-----  1 syslog adm       0 2007-10-15 16:18 mail.err
-rw-r-----  1 syslog adm       0 2007-10-15 16:18 lpr.log
-rw-r--r--  1 root   root  38607 2007-10-15 16:18 bootstrap.log
-rw-r--r--  1 root   root      0 2007-10-15 16:20 pycentral.log
-rw-r--r--  1 root   root   3113 2007-10-15 16:30 fontconfig.log
-rw-r--r--  1 root   root    308 2007-10-15 16:30 wvdialconf.log
drwxr-xr-x 15 root   root   4096 2007-10-15 16:31 ..
-rw-rw-r--  1 root   utmp 292292 2008-03-03 08:45 lastlog
-rw-r--r--  1 root   root  24024 2008-03-03 08:45 faillog
drwxr-xr-x  2 root   root   4096 2008-03-03 08:50 installer
drwxr-sr-x  2 news   news   4096 2008-03-03 09:00 news
-rw-r-----  1 root   adm     141 2008-03-06 11:09 apport.log.7.gz
-rw-r-----  1 root   adm     226 2008-03-08 01:20 apport.log.6.gz
-rw-r-----  1 root   adm     219 2008-03-08 22:22 apport.log.5.gz
-rw-r-----  1 syslog adm    1176 2008-03-09 16:00 user.log.3.gz
-rw-r-----  1 syslog adm   20154 2008-03-09 22:15 debug.3.gz
-rw-r-----  1 syslog adm   44572 2008-03-09 22:15 daemon.log.3.gz
-rw-r-----  1 syslog adm    2768 2008-03-10 00:17 auth.log.3.gz
-rw-r-----  1 root   adm    2062 2008-03-10 00:18 acpid.4.gz
-rw-r-----  1 syslog adm  101073 2008-03-10 00:23 messages.3.gz
-rw-r-----  1 syslog adm  109059 2008-03-10 00:26 kern.log.3.gz
-rw-r-----  1 root   adm   84939 2008-03-11 11:51 dpkg.log.2.gz
-rw-rw-r--  1 root   utmp      0 2008-03-12 08:17 btmp.1
-rw-r-----  1 root   adm   15174 2008-03-16 13:06 acpid.3.gz
-rw-r--r--  1 root   root      0 2008-03-16 13:12 scrollkeeper.log.2
-rw-r-----  1 syslog adm    2143 2008-03-17 01:28 auth.log.2.gz
-rw-r-----  1 root   adm     162 2008-03-17 01:28 apport.log.4.gz
-rw-r-----  1 syslog adm     570 2008-03-17 13:20 user.log.2.gz
-rw-r-----  1 syslog adm   22116 2008-03-17 13:20 debug.2.gz
-rw-r-----  1 syslog adm   39474 2008-03-17 13:20 daemon.log.2.gz
-rw-r-----  1 syslog adm   99183 2008-03-17 13:21 kern.log.2.gz
-rw-r-----  1 syslog adm   89704 2008-03-17 13:27 messages.2.gz
-rw-r-----  1 root   adm   16995 2008-03-23 10:55 acpid.2.gz
-rw-r--r--  1 root   root      0 2008-03-23 11:00 scrollkeeper.log.1
-rw-r-----  1 root   adm     161 2008-03-24 00:28 apport.log.3.gz
-rw-r-----  1 syslog adm    1032 2008-03-24 18:42 user.log.1.gz
-rw-r-----  1 syslog adm   98422 2008-03-24 18:42 kern.log.1.gz
-rw-r-----  1 syslog adm   17393 2008-03-24 18:42 debug.1.gz
-rw-r-----  1 syslog adm   30167 2008-03-24 18:42 daemon.log.1.gz
-rw-r-----  1 syslog adm   92626 2008-03-24 18:48 messages.1.gz
-rw-r-----  1 syslog adm    2134 2008-03-24 18:50 auth.log.1.gz
-rw-r-----  1 root   adm     231 2008-03-24 19:01 apport.log.2.gz
-rw-r-----  1 syslog adm   15486 2008-03-26 09:53 syslog.6.gz
-rw-r-----  1 syslog adm   17667 2008-03-27 15:18 syslog.5.gz
-rw-r-----  1 syslog adm   14207 2008-03-28 06:14 syslog.4.gz
-rw-r-----  1 syslog adm   54424 2008-03-29 18:50 syslog.3.gz
-rw-r-----  1 root   adm   29778 2008-03-29 18:57 dpkg.log.1
-rw-r-----  1 root   adm    7434 2008-03-30 00:27 dmesg.4.gz
-rw-r-----  1 root   adm    7372 2008-03-30 07:21 dmesg.3.gz
-rw-r-----  1 root   adm   10793 2008-03-30 07:22 acpid.1.gz
-rw-r-----  1 syslog adm   36941 2008-03-30 07:26 syslog.2.gz
-rw-r--r--  1 root   root      0 2008-03-30 07:26 scrollkeeper.log
-rw-r-----  1 root   adm    7649 2008-03-30 16:25 dmesg.2.gz
-rw-r-----  1 root   adm    7585 2008-03-31 09:35 dmesg.1.gz
-rw-r-----  1 syslog adm   19023 2008-03-31 09:35 auth.log.0
-rw-r-----  1 syslog adm    9714 2008-03-31 09:36 user.log.0
-rw-r-----  1 syslog adm  493199 2008-03-31 09:36 daemon.log.0
-rw-r-----  1 syslog adm  537110 2008-03-31 09:36 kern.log.0
-rw-r-----  1 syslog adm  306322 2008-03-31 09:36 debug.0
-rw-r-----  1 syslog adm   28119 2008-03-31 09:40 syslog.1.gz
-rw-r-----  1 syslog adm  493988 2008-03-31 09:41 messages.0
drwxr-x---  3 root   adm    4096 2008-03-31 09:53 samba
-rw-r-----  1 root   adm     300 2008-03-31 17:34 apport.log.1
-rw-r-----  1 root   adm   21352 2008-03-31 21:57 dmesg.0
-rw-r--r--  1 root   root  52055 2008-03-31 23:56 Xorg.0.log.old
-rw-r--r--  1 root   root 315961 2008-04-01 11:41 udev
-rw-r-----  1 root   adm   22243 2008-04-01 11:41 dmesg
drwxr-xr-x  2 root   root   4096 2008-04-01 11:41 gdm
-rw-rw-r--  1 root   utmp 142848 2008-04-01 11:42 wtmp.1
-rw-r-----  1 syslog adm    1715 2008-04-01 11:42 user.log
-rw-r-----  1 syslog adm   76272 2008-04-01 11:43 daemon.log
-rw-r-----  1 syslog adm   93870 2008-04-01 11:43 kern.log
-rw-r-----  1 syslog adm   51096 2008-04-01 11:43 debug
-rw-r-----  1 syslog adm  175795 2008-04-01 11:46 syslog.0
drwxr-xr-x  2 root   root   4096 2008-04-01 11:46 cups
drwxr-xr-x  2 root   root   4096 2008-04-01 11:46 apt
-rw-r-----  1 root   adm       0 2008-04-01 11:46 apport.log
-rw-r-----  1 root   adm       0 2008-04-01 11:46 dpkg.log
-rw-rw-r--  1 root   utmp      0 2008-04-01 11:46 btmp
drwxr-xr-x 12 root   root   4096 2008-04-01 11:48 .
-rw-r-----  1 syslog adm    3229 2008-04-01 12:17 auth.log
-rw-r-----  1 root   adm   66295 2008-04-01 12:18 acpid
-rw-r-----  1 syslog adm     400 2008-04-01 12:41 syslog
-rw-r-----  1 syslog adm   85967 2008-04-01 12:41 messages
-rw-r--r--  1 root   root  57277 2008-04-01 12:57 Xorg.0.log
-rw-rw-r--  1 root   utmp    384 2008-04-01 12:58 wtmp

```

---

### Post by roelpeeters on 2008-04-01
You could start with 
```

tail messages

```

which should show the last 20 or so kernel messages. This file contains the timestamp of each message, and therefore you can see what action took a long time, or even if time outs occurred. You'd have to do some forensic work here, to find out exactly what happened ....

Any of the other files that are on the bottom of the list are the last ones that were modified. Take a look inside them, paying attention especially to the timestamp of the messages inside.

HTH

---

### Post by SoDanishWasLike on 2008-04-02
I punched in "tail messages" in the terminal and got an error.... what did I do wrong?

---

### Post by roelpeeters on 2008-04-03
OK, looking at your directory output, it shows that the owner of the messages file is sysadm. Therefore you should use:
```

sudo tail messages

```

Otherwise you can use the command
```

dmesg

```

You can try also with the other files that are listed last.

---

