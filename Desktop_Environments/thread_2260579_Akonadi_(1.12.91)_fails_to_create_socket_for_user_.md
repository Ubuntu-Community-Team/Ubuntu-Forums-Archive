---
title: "Akonadi (1.12.91) fails to create socket for user with space in name"
date: 2015-01-13
forum: Desktop Environments
---

### Post by mbajzh on 2015-01-13
I am using Ubuntu 14.10 with kubuntu-desktop installed, my machine is a member of a domain (connected using pbis-open).   My domain username is "forename[space]surname", which is fine for the majority of scenarios, however the akonadi socket seems to be derived from the username and fails to correctly escape the space.

```
150113  6:37:18 InnoDB: Completed initialization of buffer pool
150113  6:37:18 InnoDB: highest supported file format is Barracuda.
150113  6:37:18  InnoDB: Waiting for the background threads to start
150113  6:37:19 InnoDB: 5.5.40 started; log sequence number 1595916
/usr/sbin/mysqld: Too many arguments (first extra is '***MYSURNAME***.1nvgn6/mysql.socket').
Use --verbose --help to get a list of available options
150113  6:37:19 [ERROR] Aborting


150113  6:37:19  InnoDB: Starting shutdown...
150113  6:37:20  InnoDB: Shutdown completed; log sequence number 1595916
150113  6:37:20 [Note] /usr/sbin/mysqld: Shutdown complete

```

Where the socket is shown in the rc file to be:

```

[%General]
Driver=QMYSQL


[QMYSQL]
Name=akonadi
Host=
Options="UNIX_SOCKET=/tmp/akonadi-***forename*** ***surname***.1nvgn6/mysql.socket"
ServerPath=/usr/sbin/mysqld-akonadi
StartServer=true

```

I have changed the socket defined in the rcfile and chowned it to root (to prevent it from being overwritten), but akonadictl start seems to be getting it from elsewhere!

I have tried changing the pbis configurable "SpaceReplacement" character to an underscore, but (oddly) this has had no effect on this issue (but has broken other things).

Does anybody know of any way of influencing the socket name (using the ubuntu packaged version of akonadi as opposed to installing from source) so that I can get round this?

---

