---
title: "akonadi-sqlite no longer adequate?"
date: 2012-04-16
forum: Desktop Environments
---

### Post by awry on 2012-04-16
Now that kde-4.8.2 has hit the kubuntu-backports ppa, I have a problem.

Prior to 4.8.2, akonadi-server was happy to install with akonadi-backend-sqlite. 

With the 4.8.2 packages, however, akonadi-backend-mysql appears to have been added as a hard dependency.

I really, strenuously object to running a dedicated mysql instance for my Desktop to operate properly.

Does anybody know why this dependency changed? Is this an upstream issue, or a packaging issue?

---

### Post by awry on 2012-04-16
I might add, despite strenuously objecting to having to run a dedicated mysql instance for my desktop, that I cannot even install akonadi-backend-mysql, because I require percona server for other applications.

akonadi-backend-mysql depends on mysql-server-core-5.1, which attempts to write /usr/sbin/mysqld. But mysqld already exists and is owned by the percona-server-server-5.1 package, so akonadi-backend-mysql is a nonstarter for me.

Ultimately there needs to be some coordination, methinks, between Percona and debian/ubuntu on packaging. 

But in the meantime, it would be nice to have a usable desktop.

---

### Post by Zorael on 2012-04-17
From the Akonadi changelogs (admittedly precise and not oneiric);
```
akonadi (1.7.0-0ubuntu3) precise; urgency=low

  * make akonadi-server require the mysql backend. It's the only one really
    supported upstream and as the default backend has to be installed.
    (LP: [#923189](https://bugs.launchpad.net/ubuntu/+source/akonadi/+bug/923189))

 -- Philip Muškovac <yofel@kubuntu.org>  Mon, 09 Apr 2012 18:49:42 +0200
```
Small sidenote; it seems the kcm (configuration window) is bugged so you can't choose between any backend other than mysql or postgresql. I filed this as [bko #298314](https://bugs.kde.org/show_bug.cgi?id=298314).

I'm far from an authority on this but yes, I believe this is a packaging bug. Just as you say; in the current scheme **akonadi-server** cannot be installed if **mysql-server-core-5.1** and **mysql-client-core-5.1** cannot in turn be installed -- and **kdepim-runtime** and other core KDE packages depend on **akonadi-server**.

As a test I [modified](http://pastie.org/3805783) (the packaging of) akonadi-server to instead depend on a fictive '*akonadi-backend*' virtual package, and then modified the backends in turn to [provide](http://www.debian.org/doc/debian-policy/ch-relationships.html#s-virtual) that package. I built it locally and from what I can see, it works well.

With some extraoneous lines removed;
```
$ **dpkg -l akonadi***
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                       Version                    Description
+++-==========================-==========================-====================================================================
**[COLOR="Red"]un[/COLOR]**  akonadi-backend-mysql      <none>                     (no description available)
**[COLOR="Red"]un[/COLOR]**  akonadi-backend-odbc       <none>                     (no description available)
**[COLOR="Red"]un[/COLOR]**  akonadi-backend-postgresql <none>                     (no description available)
**[COLOR="Green"]ii[/COLOR]**  akonadi-backend-**sqlite**     1.7.2-0ubuntu1.1~zor03     SQLite storage backend for Akonadi
ii  akonadi-dbg                1.7.2-0ubuntu1.1~zor03     debugging symbols for the Akonadi PIM storage service
**[COLOR="Green"]ii[/COLOR]**  akonadi-server             1.7.2-0ubuntu1.1~zor03     Akonadi PIM storage service


$ **dpkg -l mysql-*-core-5.1**
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                       Version                    Description
+++-==========================-==========================-====================================================================
**[COLOR="Red"]un[/COLOR]**  mysql-client-core-5.1      <none>                     (no description available)
**[COLOR="Red"]un[/COLOR]**  mysql-server-core-5.1      <none>                     (no description available)
```
Only the sqlite backend is installed, mysql stays at home, and akonadi-server itself is happy. Naturally you can't set akonadi to actually *use* the sqlite backend via its configuration window (because of the aforementioned bug), but you can manually edit **~/.config/akonadi/akonadiserverrc** as a workaround. At the very top;
```
**[%General]**
*# available drivers are: QSQLITE, QMYSQL3, QMYSQL, QSQLITE3*
Driver=**QSQLITE3**
```

I mentioned this in [**#kubuntu-devel**](irc://irc.freenode.net/kubuntu-devel), but most people seemed busy. **yofel** there suggested to file a Launchpad bug, so I'll do that tomorrow.

---

### Post by awry on 2012-04-17
Zorael: thanks for confirming the bug and offering a solution. I'll give this approach a try when I get home. I knew there had to be some workaround, but hadn't thought to create a new virtual package for akonadi-backend.

There's been a (poorly named) [bug]("https://bugs.launchpad.net/percona-server/+bug/521788") filed against percona-server. I just added kubuntu-ppa to the list of affected projects.

Cheers!

---

### Post by Zorael on 2012-04-26
Apologies; I've been a mite busy. Finally got around to filing the bug.

[palindrome LP **#988889** [akonadi-server]: "[packaging] hard dependency on mysql backend, breaks other programs"](https://bugs.launchpad.net/ubuntu/+source/akonadi/+bug/988889)

---

