---
title: "mail? i never set up mail. what is this?"
date: 2005-12-07
forum: Desktop Environments
---

### Post by 0okami on 2005-12-07
OK! odd problem which possibly has a simple solution. 

Im seeing that GKrellM is showing that i have 21/21 mail. 
I never set up any mail functions. 

I browsed over to ookami@Navi:/var/spool/mail$
and did: sudo gedit ookami

The contents is whats followed: 

```

From root@localhost.localdomain  Wed Nov 16 07:35:36 2005
Return-Path: <root@localhost.localdomain>
X-Original-To: root
Delivered-To: root@localhost.localdomain
Received: by localhost.localdomain (Postfix, from userid 0)
	id 4288A7B012E; Wed, 16 Nov 2005 07:35:36 -0500 (EST)
From: Anacron <root@localhost.localdomain>
To: root@localhost.localdomain
Subject: Anacron job 'cron.daily' on Navi
Message-Id: <20051116123536.4288A7B012E@localhost.localdomain>
Date: Wed, 16 Nov 2005 07:35:36 -0500 (EST)

/etc/cron.daily/man-db:
mandb: warning: /usr/share/man/man1/rmic.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/rmiregistry.1.gz is a dangling symlink

From root@localhost.localdomain  Wed Nov 16 07:40:04 2005
Return-Path: <root@localhost.localdomain>
X-Original-To: root
Delivered-To: root@localhost.localdomain
Received: by localhost.localdomain (Postfix, from userid 0)
	id 657B47B012E; Wed, 16 Nov 2005 07:40:04 -0500 (EST)
From: Anacron <root@localhost.localdomain>
To: root@localhost.localdomain
Subject: Anacron job 'cron.weekly' on Navi
Message-Id: <20051116124004.657B47B012E@localhost.localdomain>
Date: Wed, 16 Nov 2005 07:40:04 -0500 (EST)

/etc/cron.weekly/man-db:
mandb: warning: /usr/share/man/man1/rmic.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/rmiregistry.1.gz is a dangling symlink

From root@localhost.localdomain  Wed Nov 16 11:01:20 2005
Return-Path: <root@localhost.localdomain>
X-Original-To: root
Delivered-To: root@localhost.localdomain
Received: by localhost.localdomain (Postfix, from userid 0)
	id 6648E7B016D; Wed, 16 Nov 2005 11:01:17 -0500 (EST)
To: root@localhost.localdomain
Subject: WARNING: mysqlcheck has found corrupt tables
Message-Id: <20051116160117.6648E7B016D@localhost.localdomain>
Date: Wed, 16 Nov 2005 11:01:17 -0500 (EST)
From: root@localhost.localdomain (root)

mythconverg.dtv_privatetypes
warning  : 1 client is using or hasn't closed the table properly
mythconverg.profilegroups
warning  : 1 client is using or hasn't closed the table properly
mythconverg.recordingprofiles
warning  : 1 client is using or hasn't closed the table properly
mythconverg.settings
warning  : 1 client is using or hasn't closed the table properly

 Improperly closed tables are also reported if clients are accessing
 the tables *now*. A list of current connections is below.

+----+------------------+-----------+----+---------+------+-------+------------------+
| Id | User             | Host      | db | Command | Time | State | Info             |
+----+------------------+-----------+----+---------+------+-------+------------------+
| 5  | debian-sys-maint | localhost |    | Query   | 0    |       | show processlist |
+----+------------------+-----------+----+---------+------+-------+------------------+
Uptime: 2  Threads: 1  Questions: 65  Slow queries: 0  Opens: 57  Flush tables: 1  Open tables: 51  Queries per second avg: 32.500

From root@localhost.localdomain  Thu Nov 17 06:33:38 2005
Return-Path: <root@localhost.localdomain>
X-Original-To: root
Delivered-To: root@localhost.localdomain
Received: by localhost.localdomain (Postfix, from userid 0)
	id 1E4ED7B0171; Thu, 17 Nov 2005 06:33:37 -0500 (EST)
From: Anacron <root@localhost.localdomain>
To: root@localhost.localdomain
Subject: Anacron job 'cron.daily' on Navi
Message-Id: <20051117113337.1E4ED7B0171@localhost.localdomain>
Date: Thu, 17 Nov 2005 06:33:37 -0500 (EST)

/etc/cron.daily/man-db:
mandb: warning: /usr/share/man/man1/rmic.1.gz is a dangling symlink


From root@localhost.localdomain  Sat Nov 19 09:03:37 2005
Return-Path: <root@localhost.localdomain>
X-Original-To: root
Delivered-To: root@localhost.localdomain
Received: by localhost.localdomain (Postfix, from userid 0)
	id 959957B0131; Sat, 19 Nov 2005 09:03:36 -0500 (EST)
From: Anacron <root@localhost.localdomain>
To: root@localhost.localdomain
Subject: Anacron job 'cron.daily' on Navi
Message-Id: <20051119140336.959957B0131@localhost.localdomain>
Date: Sat, 19 Nov 2005 09:03:36 -0500 (EST)

/etc/cron.daily/man-db:
mandb: warning: /usr/share/man/man1/rmic.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/rmiregistry.1.gz is a dangling symlink

From root@localhost.localdomain  Sun Nov 20 07:35:22 2005
Return-Path: <root@localhost.localdomain>
X-Original-To: root
Delivered-To: root@localhost.localdomain
Received: by localhost.localdomain (Postfix, from userid 0)
	id 0A3677B016D; Sun, 20 Nov 2005 07:35:21 -0500 (EST)
From: Anacron <root@localhost.localdomain>
To: root@localhost.localdomain
Subject: Anacron job 'cron.daily' on Navi
Message-Id: <20051120123521.0A3677B016D@localhost.localdomain>
Date: Sun, 20 Nov 2005 07:35:21 -0500 (EST)

/etc/cron.daily/man-db:
mandb: warning: /usr/share/man/man1/rmic.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/rmiregistry.1.gz is a dangling symlink

From root@localhost.localdomain  Mon Nov 21 07:35:52 2005
Return-Path: <root@localhost.localdomain>
X-Original-To: root
Delivered-To: root@localhost.localdomain
Received: by localhost.localdomain (Postfix, from userid 0)
	id 97AD57B0163; Mon, 21 Nov 2005 07:35:52 -0500 (EST)
From: Anacron <root@localhost.localdomain>
To: root@localhost.localdomain
Subject: Anacron job 'cron.daily' on Navi
Message-Id: <20051121123552.97AD57B0163@localhost.localdomain>
Date: Mon, 21 Nov 2005 07:35:52 -0500 (EST)

/etc/cron.daily/man-db:
mandb: warning: /usr/share/man/man1/rmic.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/rmiregistry.1.gz is a dangling symlink

From root@localhost.localdomain  Wed Nov 23 02:46:13 2005
Return-Path: <root@localhost.localdomain>
X-Original-To: root
Delivered-To: root@localhost.localdomain
Received: by localhost.localdomain (Postfix, from userid 0)
	id 8003D7B0167; Wed, 23 Nov 2005 02:46:13 -0500 (EST)
From: Anacron <root@localhost.localdomain>
To: root@localhost.localdomain
Subject: Anacron job 'cron.daily' on Navi
Message-Id: <20051123074613.8003D7B0167@localhost.localdomain>
Date: Wed, 23 Nov 2005 02:46:13 -0500 (EST)

/etc/cron.daily/man-db:
mandb: warning: /usr/share/man/man1/rmic.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/rmiregistry.1.gz is a dangling symlink

From root@localhost.localdomain  Thu Nov 24 05:20:57 2005
Return-Path: <root@localhost.localdomain>
X-Original-To: root
Delivered-To: root@localhost.localdomain
Received: by localhost.localdomain (Postfix, from userid 0)
	id B6E8B7B0161; Thu, 24 Nov 2005 05:20:57 -0500 (EST)
From: Anacron <root@localhost.localdomain>
To: root@localhost.localdomain
Subject: Anacron job 'cron.daily' on Navi
Message-Id: <20051124102057.B6E8B7B0161@localhost.localdomain>
Date: Thu, 24 Nov 2005 05:20:57 -0500 (EST)

/etc/cron.daily/man-db:
mandb: warning: /usr/share/man/man1/rmic.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/rmiregistry.1.gz is a dangling symlink

From root@localhost.localdomain  Fri Nov 25 07:39:32 2005
Return-Path: <root@localhost.localdomain>
X-Original-To: root
Delivered-To: root@localhost.localdomain
Received: by localhost.localdomain (Postfix, from userid 0)
	id 158537B0163; Fri, 25 Nov 2005 07:39:31 -0500 (EST)
From: Anacron <root@localhost.localdomain>
To: root@localhost.localdomain
Subject: Anacron job 'cron.daily' on Navi
Message-Id: <20051125123931.158537B0163@localhost.localdomain>
Date: Fri, 25 Nov 2005 07:39:31 -0500 (EST)

/etc/cron.daily/man-db:
mandb: warning: /usr/share/man/man1/rmic.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/rmiregistry.1.gz is a dangling symlink

From root@localhost.localdomain  Sat Nov 26 06:33:13 2005
Return-Path: <root@localhost.localdomain>
X-Original-To: root
Delivered-To: root@localhost.localdomain
Received: by localhost.localdomain (Postfix, from userid 0)
	id 59DD67B0165; Sat, 26 Nov 2005 06:33:13 -0500 (EST)
From: Anacron <root@localhost.localdomain>
To: root@localhost.localdomain
Subject: Anacron job 'cron.daily' on Navi
Message-Id: <20051126113313.59DD67B0165@localhost.localdomain>
Date: Sat, 26 Nov 2005 06:33:13 -0500 (EST)

/etc/cron.daily/man-db:
mandb: warning: /usr/share/man/man1/rmic.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/rmiregistry.1.gz is a dangling symlink

From root@localhost.localdomain  Sun Nov 27 07:35:51 2005
Return-Path: <root@localhost.localdomain>
X-Original-To: root
Delivered-To: root@localhost.localdomain
Received: by localhost.localdomain (Postfix, from userid 0)
	id 865747B0167; Sun, 27 Nov 2005 07:35:50 -0500 (EST)
From: Anacron <root@localhost.localdomain>
To: root@localhost.localdomain
Subject: Anacron job 'cron.daily' on Navi
Message-Id: <20051127123550.865747B0167@localhost.localdomain>
Date: Sun, 27 Nov 2005 07:35:50 -0500 (EST)

/etc/cron.daily/man-db:
mandb: warning: /usr/share/man/man1/rmic.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/rmiregistry.1.gz is a dangling symlink

From root@localhost.localdomain  Sun Nov 27 08:29:10 2005
Return-Path: <root@localhost.localdomain>
X-Original-To: root
Delivered-To: root@localhost.localdomain
Received: by localhost.localdomain (Postfix, from userid 0)
	id 62ABE7B0167; Sun, 27 Nov 2005 08:29:10 -0500 (EST)
To: root@localhost.localdomain
Subject: Debconf: Configuring msttcorefonts -- These fonts are not free.
Message-Id: <20051127132910.62ABE7B0167@localhost.localdomain>
Date: Sun, 27 Nov 2005 08:29:10 -0500 (EST)
From: root@localhost.localdomain (root)

These fonts were provided by Microsoft "in the interest of cross-platform
compatibility". This is no longer the case, but they are still available
from third parties.

You are free to download these fonts and use them for your own use, but
you may not redistribute them in modified form, including changes to the
file name or packaging format.

-- 
Debconf, running at localhost.localdomain
[ Debconf was not configured to display this note, so it mailed it to you. ]

From root@localhost.localdomain  Sun Nov 27 08:29:12 2005
Return-Path: <root@localhost.localdomain>
X-Original-To: root
Delivered-To: root@localhost.localdomain
Received: by localhost.localdomain (Postfix, from userid 0)
	id D94527B0167; Sun, 27 Nov 2005 08:29:12 -0500 (EST)
To: root@localhost.localdomain
Subject: Debconf: Configuring msttcorefonts -- These fonts are not free.
Message-Id: <20051127132912.D94527B0167@localhost.localdomain>
Date: Sun, 27 Nov 2005 08:29:12 -0500 (EST)
From: root@localhost.localdomain (root)

These fonts were provided by Microsoft "in the interest of cross-platform
compatibility". This is no longer the case, but they are still available
from third parties.

You are free to download these fonts and use them for your own use, but
you may not redistribute them in modified form, including changes to the
file name or packaging format.

-- 
Debconf, running at localhost.localdomain
[ Debconf was not configured to display this note, so it mailed it to you. ]

From root@localhost.localdomain  Mon Nov 28 07:35:54 2005
Return-Path: <root@localhost.localdomain>
X-Original-To: root
Delivered-To: root@localhost.localdomain
Received: by localhost.localdomain (Postfix, from userid 0)
	id 4F8567B015C; Mon, 28 Nov 2005 07:35:54 -0500 (EST)
From: Anacron <root@localhost.localdomain>
To: root@localhost.localdomain
Subject: Anacron job 'cron.daily' on Navi
Message-Id: <20051128123554.4F8567B015C@localhost.localdomain>
Date: Mon, 28 Nov 2005 07:35:54 -0500 (EST)

/etc/cron.daily/man-db:
mandb: warning: /usr/share/man/man1/rmic.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/rmiregistry.1.gz is a dangling symlink

From root@localhost.localdomain  Tue Nov 29 07:36:12 2005
Return-Path: <root@localhost.localdomain>
X-Original-To: root
Delivered-To: root@localhost.localdomain
Received: by localhost.localdomain (Postfix, from userid 0)
	id E84667B015D; Tue, 29 Nov 2005 07:36:11 -0500 (EST)
From: Anacron <root@localhost.localdomain>
To: root@localhost.localdomain
Subject: Anacron job 'cron.daily' on Navi
Message-Id: <20051129123611.E84667B015D@localhost.localdomain>
Date: Tue, 29 Nov 2005 07:36:11 -0500 (EST)

/etc/cron.daily/man-db:
mandb: warning: /usr/share/man/man1/rmic.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/rmiregistry.1.gz is a dangling symlink

From root@localhost.localdomain  Wed Nov 30 07:35:48 2005
Return-Path: <root@localhost.localdomain>
X-Original-To: root
Delivered-To: root@localhost.localdomain
Received: by localhost.localdomain (Postfix, from userid 0)
	id D59437B015E; Wed, 30 Nov 2005 07:35:48 -0500 (EST)
From: Anacron <root@localhost.localdomain>
To: root@localhost.localdomain
Subject: Anacron job 'cron.daily' on Navi
Message-Id: <20051130123548.D59437B015E@localhost.localdomain>
Date: Wed, 30 Nov 2005 07:35:48 -0500 (EST)

/etc/cron.daily/man-db:
mandb: warning: /usr/share/man/man1/rmic.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/rmiregistry.1.gz is a dangling symlink

From root@localhost.localdomain  Fri Dec  2 07:36:41 2005
Return-Path: <root@localhost.localdomain>
X-Original-To: root
Delivered-To: root@localhost.localdomain
Received: by localhost.localdomain (Postfix, from userid 0)
	id A0C537B0160; Fri,  2 Dec 2005 07:36:41 -0500 (EST)
From: Anacron <root@localhost.localdomain>
To: root@localhost.localdomain
Subject: Anacron job 'cron.daily' on Navi
Message-Id: <20051202123641.A0C537B0160@localhost.localdomain>
Date: Fri,  2 Dec 2005 07:36:41 -0500 (EST)

/etc/cron.daily/man-db:
mandb: warning: /usr/share/man/man1/rmic.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/rmiregistry.1.gz is a dangling symlink

From root@localhost.localdomain  Sun Dec  4 07:03:00 2005
Return-Path: <root@localhost.localdomain>
X-Original-To: root
Delivered-To: root@localhost.localdomain
Received: by localhost.localdomain (Postfix, from userid 0)
	id BCEA07B015C; Sun,  4 Dec 2005 07:03:00 -0500 (EST)
From: Anacron <root@localhost.localdomain>
To: root@localhost.localdomain
Subject: Anacron job 'cron.daily' on Navi
Message-Id: <20051204120300.BCEA07B015C@localhost.localdomain>
Date: Sun,  4 Dec 2005 07:03:00 -0500 (EST)

/etc/cron.daily/man-db:
mandb: warning: /usr/share/man/man1/rmic.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/rmiregistry.1.gz is a dangling symlink

From root@localhost.localdomain  Mon Dec  5 07:36:15 2005
Return-Path: <root@localhost.localdomain>
X-Original-To: root
Delivered-To: root@localhost.localdomain
Received: by localhost.localdomain (Postfix, from userid 0)
	id 6D1207B015D; Mon,  5 Dec 2005 07:36:15 -0500 (EST)
From: Anacron <root@localhost.localdomain>
To: root@localhost.localdomain
Subject: Anacron job 'cron.daily' on Navi
Message-Id: <20051205123615.6D1207B015D@localhost.localdomain>
Date: Mon,  5 Dec 2005 07:36:15 -0500 (EST)

/etc/cron.daily/man-db:
mandb: warning: /usr/share/man/man1/rmic.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/rmiregistry.1.gz is a dangling symlink

From root@localhost.localdomain  Tue Dec  6 07:36:14 2005
Return-Path: <root@localhost.localdomain>
X-Original-To: root
Delivered-To: root@localhost.localdomain
Received: by localhost.localdomain (Postfix, from userid 0)
	id 804617B015E; Tue,  6 Dec 2005 07:36:13 -0500 (EST)
From: Anacron <root@localhost.localdomain>
To: root@localhost.localdomain
Subject: Anacron job 'cron.daily' on Navi
Message-Id: <20051206123613.804617B015E@localhost.localdomain>
Date: Tue,  6 Dec 2005 07:36:13 -0500 (EST)

/etc/cron.daily/man-db:
mandb: warning: /usr/share/man/man1/rmic.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/rmiregistry.1.gz is a dangling symlink


```


I have no idea what ^that is about. Could someone explain so i can make heads/tails of this?

thanks'

---

### Post by invalid on 2005-12-07
Certain things run automatically daily on your system. They are there to just run checks to make sure things are properly working. If they find a problem, they mail them to you to let you know.

You can check your mail by typing```
mail
``` in a terminal. If you would like a more user friendly interface, you can install mutt.```
sudo apt-get install mutt
mutt
```

The warnings in your spool look just to be that, warnings. Nothing serious is going on, so you probably do not need to worry anything about them. (Someone correct me if I am wrong!)

Hope this helps,

Cb

---

### Post by Rinzwind on 2005-12-07
Ofcourse you set up these mail functions cuz it's a normal feature: you get these messages as a report from a cron-job. Man-db is responsible for your ma(nual) pages. 

This page tells the same but it is about openoffice.org: [http://lists.ubuntulinux.org/archives/ubuntu-users/2005-April/033051.html](http://lists.ubuntulinux.org/archives/ubuntu-users/2005-April/033051.html)

But the following explains what's happening:

> ...
It means that file A is a symlink to file B which is (more or less) a
symlink pointing back to A!  (The message above as delivered to you by
"cron" (or anacron), which is a daemon running in the background running
specific tasks at a predefined date/time, usually system maintenance
tasks.  In the above message, for example, cron is running the script
"/etc/cron.daily/man-db" which is to create the mandb (man database) so
that searching the manuals by using "man -k keyword" become possible and
fast.)...


And in the follow-up is says this is a sollution:
[http://lists.ubuntulinux.org/archives/ubuntu-users/2005-April/033054.html](http://lists.ubuntulinux.org/archives/ubuntu-users/2005-April/033054.html)
[http://lists.ubuntulinux.org/archives/ubuntu-users/2005-April/033090.html](http://lists.ubuntulinux.org/archives/ubuntu-users/2005-April/033090.html)
> 
After I read both your messages, I did a little search and apparently
the two conditions are both considered "dangling links".  I did this
small test to make sure:
        mkdir ~/tmp_dir && cd ~/tmp_dir
        ln -s A B
        ln -s B A
        ln -s dead_link link
        cleanlinks ~/tmp_dir

Look at the output of that (for more information about "cleanlinks" do a
"man cleanlinks").

For your problem A would be rmic and B would be rmiregistry.

Mind you: I am still a newbie so if anyone else decides it's rubbish trust them ;)




edit:

lol I have the same message:
> 
rinzwind@Diskworld:~$ man rmic
man: warning: /usr/share/man/man1/rmic.1.gz is a dangling symlink
No manual entry for rmic

Thanks for pointing it out to me :D

edit2:
Another topic with a good explanation of the concept:
[http://lists.debian.org/debian-user/2003/10/msg00546.html](http://lists.debian.org/debian-user/2003/10/msg00546.html)

And here's where the problem is:
> rinzwind@Diskworld:/etc/alternatives$ man rmic
man: warning: /usr/share/man/man1/rmic.1.gz is a dangling symlink
No manual entry for rmic
<..>
rinzwind@Diskworld:/usr/share/man$ ls -l /usr/share/man/man1/rmic.1.gz
lrwxrwxrwx  1 root root 27 2005-12-04 12:39 /usr/share/man/man1/rmic.1.gz -> /etc/alternatives/rmic.1.gz
rinzwind@Diskworld:/usr/share/man$ ls -l /etc/alternatives/rmic.1.gz
lrwxrwxrwx  1 root root 40 2005-12-04 12:39 /etc/alternatives/rmic.1.gz -> /usr/lib/jvm/java-gcj/man/man1/rmic.1.gz
rinzwind@Diskworld:/usr/share/man$ ls -l /usr/lib/jvm/java-gcj/man/man1/rmic.1.gz
**ls: /usr/lib/jvm/java-gcj/man/man1/rmic.1.gz: No such file or directory**
rinzwind@Diskworld:/usr/share/man$ 

The links end at a dead end when it can't find the last file :)

---

### Post by 0okami on 2005-12-07
[QUOTE=Rinzwind]Ofcourse you set up these mail functions cuz it's a normal feature: you get these messages as a report from a cron-job. Man-db is responsible for your ma(nual) pages. 

This page tells the same but it is about openoffice.org: [http://lists.ubuntulinux.org/archives/ubuntu-users/2005-April/033051.html](http://lists.ubuntulinux.org/archives/ubuntu-users/2005-April/033051.html)

But the following explains what's happening:



And in the follow-up is says this is a sollution:
[http://lists.ubuntulinux.org/archives/ubuntu-users/2005-April/033054.html](http://lists.ubuntulinux.org/archives/ubuntu-users/2005-April/033054.html)
[http://lists.ubuntulinux.org/archives/ubuntu-users/2005-April/033090.html](http://lists.ubuntulinux.org/archives/ubuntu-users/2005-April/033090.html)

For your problem A would be rmic and B would be rmiregistry.

Mind you: I am still a newbie so if anyone else decides it's rubbish trust them ;)[/QUOTE]


*crashed face first into desk* i'll re read this when im more awake. Sounds too  complex for me at the moment :P

---

### Post by Rinzwind on 2005-12-07
Hey it's 7 am here and I am WIDE awake.
Sick too but I am awake :)


I added some more stuff and it's getting easier to follow. The link in  my 2nd edit is alot more clearer to understand :)

Oh and this is the 1st time I see it too ;) I'm just strolling along with your problem :D

---

### Post by erlestau on 2006-08-21
Seems to be a bug on *java-gcj-compat* package. More on [BUG#341928]("http://lists.alioth.debian.org/pipermail/pkg-java-maintainers/2005-December/006316.html").

Try 

 # update-alternative --auto rmic

as suggested in that link.

---

