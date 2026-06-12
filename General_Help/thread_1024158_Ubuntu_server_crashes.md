---
title: "Ubuntu server crashes"
date: 2008-12-28
forum: General Help
---

### Post by Ed1000 on 2008-12-28
I need some help. My Ubuntu server (8.10) crashes/dies on me at least once a day. Very annoying. I have a monitor attached to it and when the server crashes on me it really does, no signal to th emonitor anymore, though the disks are still spinning.

I checked the log file around the crash and it shows some errors that might be the couse but I do not know what to do about it. Here are th elines from the logfile around the crash:
Dec 28 23:13:12 ubuntu postfix/cleanup[1714]: fatal: dict_open: unsupported dictionary type: mysql:  Is the postfix-mysql package installed?
Dec 28 23:13:14 ubuntu postfix/master[5495]: warning: process /usr/lib/postfix/cleanup pid 1714 exit status 1
Dec 28 23:13:14 ubuntu postfix/master[5495]: warning: /usr/lib/postfix/cleanup: bad command startup -- throttling
Dec 28 23:14:13 ubuntu postfix/cleanup[1734]: fatal: dict_open: unsupported dictionary type: mysql:  Is the postfix-mysql package installed?
Dec 28 23:14:15 ubuntu postfix/master[5495]: warning: process /usr/lib/postfix/cleanup pid 1734 exit status 1
Dec 28 23:14:15 ubuntu postfix/master[5495]: warning: /usr/lib/postfix/cleanup: bad command startup -- throttling
Dec 28 23:15:14 ubuntu postfix/cleanup[1754]: fatal: dict_open: unsupported dictionary type: mysql:  Is the postfix-mysql package installed?
Dec 28 23:15:16 ubuntu postfix/master[5495]: warning: process /usr/lib/postfix/cleanup pid 1754 exit status 1
Dec 28 23:15:16 ubuntu postfix/master[5495]: warning: /usr/lib/postfix/cleanup: bad command startup -- throttling
Dec 28 23:16:15 ubuntu postfix/cleanup[1773]: fatal: dict_open: unsupported dictionary type: mysql:  Is the postfix-mysql package installed?
Dec 28 23:16:17 ubuntu postfix/master[5495]: warning: process /usr/lib/postfix/cleanup pid 1773 exit status 1
Dec 28 23:16:17 ubuntu postfix/master[5495]: warning: /usr/lib/postfix/cleanup: bad command startup -- throttling
Dec 28 23:17:02 ubuntu /USR/SBIN/CRON[1789]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 28 23:17:16 ubuntu postfix/cleanup[1796]: fatal: dict_open: unsupported dictionary type: mysql:  Is the postfix-mysql package installed?
Dec 28 23:17:18 ubuntu postfix/master[5495]: warning: process /usr/lib/postfix/cleanup pid 1796 exit status 1
Dec 28 23:17:18 ubuntu postfix/master[5495]: warning: /usr/lib/postfix/cleanup: bad command startup -- throttling
Dec 28 23:18:18 ubuntu postfix/cleanup[1817]: fatal: dict_open: unsupported dictionary type: mysql:  Is the postfix-mysql package installed?
Dec 28 23:18:19 ubuntu postfix/master[5495]: warning: process /usr/lib/postfix/cleanup pid 1817 exit status 1
Dec 28 23:18:19 ubuntu postfix/master[5495]: warning: /usr/lib/postfix/cleanup: bad command startup -- throttling
Dec 28 23:19:19 ubuntu postfix/cleanup[1837]: fatal: dict_open: unsupported dictionary type: mysql:  Is the postfix-mysql package installed?
Dec 28 23:19:21 ubuntu postfix/master[5495]: warning: process /usr/lib/postfix/cleanup pid 1837 exit status 1
Dec 28 23:19:21 ubuntu postfix/master[5495]: warning: /usr/lib/postfix/cleanup: bad command startup -- throttling
Dec 29 00:04:47 ubuntu syslogd 1.5.0#1ubuntu1: restart.
Dec 29 00:04:48 ubuntu kernel: Inspecting /boot/System.map-2.6.24-21-generic
Dec 29 00:04:50 ubuntu kernel: Loaded 27897 symbols from /boot/System.map-2.6.24-21-generic.
Dec 29 00:04:50 ubuntu kernel: Symbols match kernel version 2.6.24.

Anybody some tips?

---

### Post by Schlandower on 2008-12-28
Hi, I had this problem +- 9 months ago, I don't remember exactly how I fixed it in the end, but to start with I disabled the "dict" settings in my postfix configuration.
I was using it for quote settings on the maildirs.
On investigation I found that we could use another setting, "mailbox_size_limit".
I am at present looking through my notes to see if I can find my solution to the problem.

Hopefully the information supplied can give you some sort of a start in the right direction.

---

### Post by Ed1000 on 2008-12-28
Thanks, I'll give it a check, once I fully understand what you are saying (I'll figure it out)

In the mean time I am still open for other solutions. I noticed I could not start my MySQL server so i tried reinstalling mysql but that did not seem to help te problem

---

### Post by Ed1000 on 2008-12-28
Unfortunately I do not recognize any 'dic'settings in my postfix config file

---

### Post by Ed1000 on 2008-12-28
OK, I might have found a solution but time will tell.
Apparently I had some 4900 emailmessages in the postgres queue. Removing them has since stopped all the postfix warnings in my syslog. Time will tell if this was a/the solution. If my server is still up and running a day from now, then that is good.
Nevertheless, the better solution ofcourse is to fix the MySQL tables, but that apparently is harder than one would think.\

Nevertheless, anybody with an other view on the problem in this thread is welcome to ventilate it.

---

### Post by Ed1000 on 2008-12-29
Apparently that was NOT the solution.
Any suggestions are still welcome

---

### Post by Ed1000 on 2009-01-05
OK, this might be it: I am using the server from a windows machine. I found the windows machine had the Vundo firus/Trojan. After I removed that (about a day ago) the server has not crashed anymore whereas before it did that 3-4 times a day.
It could be that this particular variation of the Vundo bug was launching DoS attacks that caused the server to shut down.
I am hopeful. Guess that full re-install can wait a while.

---

