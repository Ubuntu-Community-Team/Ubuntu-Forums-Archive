---
title: "So it's a bug, what to do now??"
date: 2008-12-06
forum: General Help
---

### Post by arashiko28 on 2008-12-06
I had posted this before, about the computer randomly freezing and caps lock and num lock tilting. There were a thousand of answers about the fan not working correctly or the RAM's damaged, even hard drive damage. Now, I have a brand new laptop, not refurbished with no more than 15 days of use and it happens again. Since there are so many things that "triggers" this I can't find a way to report a bug. The most common is while watching video online, either youtube or whatever, the second used to be at my old computer, scrolling on a large document. The first one already happened on the new computer. This is an old issue and it's been happening since 8.04, i thought it would be fixed but no. It has nothing to do with CPU charge, nor RAM, nor heat. I have both, CPU-RAM monitor and temp monitor, and both have always been on the usual range, no overclock, no overheating. So now what?

---

### Post by Yellow Pasque on 2008-12-06
What you are experiencing is called a kernel panic. If you can reliably reproduce it, file a bug on Launchpad with the troubleshooting info they ask for here:
[https://wiki.ubuntu.com/KernelTeamBugPolicies](https://wiki.ubuntu.com/KernelTeamBugPolicies)

---

### Post by arashiko28 on 2008-12-06
That is the big problem, even if I can identify the possible causes it happens randomly, could be days or weeks before it happens again, or a few minutes after a hard shutdown provoked by the failure.

---

### Post by Ayuthia on 2008-12-06
Have you checked /var/log/messages or any of the older dmesg logs in /var/log to see what is causing the kernel panics?  If I recall correctly they are usually logged there and most likely /var/log/kern.log.*

---

### Post by arashiko28 on 2008-12-07
I can barely understand a few words from the dmesg output, I didn't found anything that called out my attention :confused: I think it's time for me to say that I'm not an computer master, just a regular user willing to learn :p so a bit more simple english could be of a great help. If needed, I can post my dmesg output as soon as I reproduce it.

---

### Post by Ayuthia on 2008-12-07
> **arashiko28 said:**
> I can barely understand a few words from the dmesg output, I didn't found anything that called out my attention :confused: I think it's time for me to say that I'm not an computer master, just a regular user willing to learn :p so a bit more simple english could be of a great help. If needed, I can post my dmesg output as soon as I reproduce it.

That is not a problem.  When it happe can ns the next time, you can go into /var/log/dmesg.0 (that is for the previous session--the one that had the kernel panic).  At the end of the log, there should be something that says Oops or Kernel Panic and then some information that goes along with it.  Most of it will not make any sense, but somewhere in that section it should tell you what application crashed.  Of course, it never hurts to post the file here when it next happens.

---

### Post by arashiko28 on 2008-12-20
> **Ayuthia said:**
> That is not a problem.  When it happe can ns the next time, you can go into /var/log/dmesg.0 (that is for the previous session--the one that had the kernel panic).  At the end of the log, there should be something that says Oops or Kernel Panic and then some information that goes along with it.  Most of it will not make any sense, but somewhere in that section it should tell you what application crashed.  Of course, it never hurts to post the file here when it next happens.

](*,)](*,)](*,)](*,) This can't be possible!!! After about 4 days of continued work it froze this morning and the forum was down for maintenance and I saved the wrong file!

As the dmesg.0 don't have time, I don't know where to start, I have checked the entire file and haven't found the message of the crash. This time was caused by the attepmt to reconnect the wireless after a shut down of the router. :confused::(

---

### Post by Ayuthia on 2008-12-20
You might check /var/log/messages also.  It sometimes keeps logs for the last few boots.

Have you rebooted since the last crash?

---

### Post by arashiko28 on 2008-12-20
once to seek for the file and one shutdown for low batt...

---

### Post by arashiko28 on 2008-12-20
Can't open it, and when try to see it on terminal with cat /var/log/messages the list never ends, I stopped it, but the message goes missing as it grows. I cant retrieve anything before 9:02 am, the crash was a 8:57am :(
In messages.0 it's only up to yesterday.

---

### Post by Ayuthia on 2008-12-20
> **arashiko28 said:**
> Can't open it, and when try to see it on terminal with cat /var/log/messages the list never ends, I stopped it, but the message goes missing as it grows. I cant retrieve anything before 9:02 am, the crash was a 8:57am :(
In messages.0 it's only up to yesterday.

Can you post the results of:
```
ls -l /var/log
```And please let us know the date of the crash.  There might still be a log that exists there that can help.

---

### Post by arashiko28 on 2008-12-30
> ls -l /var/log
total 771288
-rw-r----- 1 root      adm      33460 2008-11-22 12:17 acpid
drwxr-xr-x 2 root      root      4096 2008-04-07 17:39 apparmor
drwxr-xr-x 2 root      root      4096 2008-12-01 08:32 apt
-rw-r----- 1 syslog    adm     120621 2008-12-30 17:20 auth.log
-rw-r----- 1 syslog    adm     235170 2008-12-26 08:00 auth.log.0
-rw-r----- 1 syslog    adm      11681 2008-12-19 03:10 auth.log.1.gz
-rw-r----- 1 syslog    adm      11609 2008-12-12 20:00 auth.log.2.gz
-rw-r----- 1 syslog    adm      13831 2008-12-05 01:40 auth.log.3.gz
-rw-r----- 1 root      adm         31 2008-04-22 13:49 boot
-rw-r--r-- 1 root      root     40690 2008-04-22 13:49 bootstrap.log
-rw-rw---- 1 root      utmp      1152 2008-12-30 12:37 btmp
-rw-rw-r-- 1 root      utmp       384 2008-11-22 12:48 btmp.1
drwxr-xr-x 2 root      root      4096 2008-11-22 12:39 ConsoleKit
drwxr-xr-x 2 root      root      4096 2008-12-30 13:22 cups
-rw-r----- 1 syslog    adm     262761 2008-12-30 17:19 daemon.log
-rw-r----- 1 syslog    adm     551005 2008-12-26 07:23 daemon.log.0
-rw-r----- 1 syslog    adm      34243 2008-12-19 03:09 daemon.log.1.gz
-rw-r----- 1 syslog    adm      42402 2008-12-12 19:47 daemon.log.2.gz
-rw-r----- 1 syslog    adm      34438 2008-12-05 01:39 daemon.log.3.gz
-rw-r----- 1 syslog    adm     208766 2008-12-30 17:19 debug
-rw-r----- 1 syslog    adm     105039 2008-12-25 22:52 debug.0
-rw-r----- 1 syslog    adm    2069507 2008-12-25 00:43 debug.1.gz
-rw-r----- 1 syslog    adm     153322 2008-12-24 08:01 debug.2.gz
-rw-r----- 1 syslog    adm     628173 2008-12-21 01:48 debug.3.gz
-rw-r----- 1 syslog    adm      50355 2008-12-12 19:57 debug.4.gz
-rw-r----- 1 syslog    adm      23462 2008-12-05 00:45 debug.5.gz
-rw-r----- 1 syslog    adm      40600 2008-11-28 00:31 debug.6.gz
drwxr-xr-x 2 root      root      4096 2008-11-22 14:25 dist-upgrade
-rw-r----- 1 root      adm      42902 2008-12-30 17:17 dmesg
-rw-r----- 1 root      adm      43257 2008-12-30 12:35 dmesg.0
-rw-r----- 1 root      adm      12182 2008-12-30 10:41 dmesg.1.gz
-rw-r----- 1 root      adm      12166 2008-12-29 17:08 dmesg.2.gz
-rw-r----- 1 root      adm      12207 2008-12-29 17:01 dmesg.3.gz
-rw-r----- 1 root      adm      12217 2008-12-29 13:09 dmesg.4.gz
-rw-r----- 1 root      adm     210067 2008-12-26 21:23 dpkg.log
-rw-r----- 1 root      adm    2108115 2008-11-29 19:09 dpkg.log.1
-rw-r--r-- 1 root      root     24048 2008-12-24 18:00 faillog
-rw-r--r-- 1 root      root      2949 2008-12-08 00:25 fontconfig.log
drwxr-xr-x 2 root      root      4096 2008-04-22 13:49 fsck
drwxr-xr-x 2 root      root      4096 2008-12-30 17:18 gdm
drwxr-xr-x 2 root      root      4096 2008-11-21 13:30 installer
-rw-r----- 1 syslog    adm    1017129 2008-12-30 17:19 kern.log
-rw-r----- 1 syslog    adm    1042699 2008-12-26 02:47 kern.log.0
-rw-r----- 1 syslog    adm  150810694 2008-12-24 10:17 kern.log.1.gz
-rw-r----- 1 syslog    adm   31461587 2008-12-24 08:04 kern.log.2.gz
-rw-r----- 1 syslog    adm  113690143 2008-12-20 11:55 kern.log.3.gz
-rw-r----- 1 syslog    adm     209511 2008-12-15 10:01 kern.log.4.gz
-rw-r----- 1 syslog    adm     157621 2008-12-12 19:57 kern.log.5.gz
-rw-r----- 1 syslog    adm     212663 2008-12-10 03:18 kern.log.6.gz
drwxr-xr-x 2 landscape root      4096 2008-11-22 12:27 landscape
-rw-rw-r-- 1 root      utmp    292584 2008-12-24 18:00 lastlog
-rw-r----- 1 syslog    adm          0 2008-04-22 13:49 lpr.log
-rw-r----- 1 syslog    adm          0 2008-04-22 13:49 mail.err
-rw-r----- 1 syslog    adm          0 2008-04-22 13:49 mail.info
-rw-r----- 1 syslog    adm          0 2008-04-22 13:49 mail.log
-rw-r----- 1 syslog    adm          0 2008-04-22 13:49 mail.warn
-rw-r----- 1 syslog    adm     822241 2008-12-30 17:19 messages
-rw-r----- 1 syslog    adm     748848 2008-12-26 07:51 messages.0
-rw-r----- 1 syslog    adm  152021602 2008-12-24 10:26 messages.1.gz
-rw-r----- 1 syslog    adm   30076688 2008-12-24 08:04 messages.2.gz
-rw-r----- 1 syslog    adm  114075729 2008-12-20 12:01 messages.3.gz
-rw-r----- 1 syslog    adm     206742 2008-12-16 09:14 messages.4.gz
-rw-r----- 1 syslog    adm     301631 2008-12-12 19:57 messages.5.gz
-rw-r----- 1 syslog    adm     233533 2008-12-05 01:40 messages.6.gz
drwxr-sr-x 2 news      news      4096 2008-11-21 17:32 news
-rw-r--r-- 1 root      root       936 2008-12-08 13:00 pm-suspend.log
-rw-r--r-- 1 root      root         0 2008-04-22 13:51 pycentral.log
drwxr-x--- 3 root      adm       4096 2008-12-28 12:40 samba
-rw-r--r-- 1 root      root         0 2008-12-28 12:40 scrollkeeper.log
-rw-r--r-- 1 root      root         0 2008-12-21 02:29 scrollkeeper.log.1
-rw-r--r-- 1 root      root         0 2008-12-14 01:34 scrollkeeper.log.2
-rw-r----- 1 syslog    adm      98567 2008-12-30 17:20 syslog
-rw-r----- 1 syslog    adm     577217 2008-12-30 13:20 syslog.0
-rw-r----- 1 syslog    adm      35769 2008-12-29 03:10 syslog.1.gz
-rw-r----- 1 syslog    adm      42024 2008-12-28 12:40 syslog.2.gz
-rw-r----- 1 syslog    adm      36542 2008-12-27 00:30 syslog.3.gz
-rw-r----- 1 syslog    adm     152542 2008-12-26 07:50 syslog.4.gz
-rw-r----- 1 syslog    adm  150810843 2008-12-24 10:17 syslog.5.gz
-rw-r----- 1 syslog    adm   31376306 2008-12-24 08:04 syslog.6.gz
-rw-r--r-- 1 root      root    413657 2008-12-30 17:17 udev
drwxr-xr-x 2 root      root      4096 2008-03-10 11:24 unattended-upgrades
-rw-r----- 1 syslog    adm      11159 2008-12-30 17:19 user.log
-rw-r----- 1 syslog    adm      18326 2008-12-25 22:20 user.log.0
-rw-r----- 1 syslog    adm       1526 2008-12-16 17:20 user.log.1.gz
-rw-r----- 1 syslog    adm       2001 2008-12-12 19:46 user.log.2.gz
-rw-r----- 1 syslog    adm       1464 2008-12-04 22:41 user.log.3.gz
-rw-r--r-- 1 root      root      3491 2008-12-30 17:21 wpa_supplicant.log
-rw-r--r-- 1 root      root       408 2008-12-30 13:20 wpa_supplicant.log.1.gz
-rw-r--r-- 1 root      root       403 2008-12-29 03:10 wpa_supplicant.log.2.gz
-rw-r--r-- 1 root      root       587 2008-12-28 12:40 wpa_supplicant.log.3.gz
-rw-r--r-- 1 root      root       343 2008-12-27 00:34 wpa_supplicant.log.4.gz
-rw-r--r-- 1 root      root       749 2008-12-26 07:46 wpa_supplicant.log.5.gz
-rw-rw-r-- 1 root      utmp    447744 2008-12-30 17:21 wtmp
-rw-rw-r-- 1 root      utmp    191232 2008-11-30 23:49 wtmp.1
-rw-r--r-- 1 root      root       350 2008-11-22 12:32 wvdialconf.log
-rw-r--r-- 1 root      root     23925 2008-12-30 17:19 Xorg.0.log
-rw-r--r-- 1 root      root     25405 2008-12-30 17:18 Xorg.0.log.old
-rw-r--r-- 1 root      root     20501 2008-11-24 23:59 Xorg.20.log
-rw-r--r-- 1 root      root     20108 2008-11-22 16:36 Xorg.20.log.old
-rw-r--r-- 1 root      root     39789 2008-12-24 18:10 Xorg.failsafe.log
-rw-r--r-- 1 root      root     39790 2008-12-24 17:59 Xorg.failsafe.log.old


I had another crash recently, I'll try to find the message.

---

