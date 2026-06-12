---
title: "tcp6, inet.d and backup"
date: 2006-10-02
forum: Desktop Environments
---

### Post by espenbe on 2006-10-02
I have a computer running Ubuntu 6.06 at the office.  Backup of this computer is supposed to be performed by the computer department every afternoon.  The problem is that the backup software can only connect using tcp4.  My Ubuntu is offering tcp6, which makes me live without backup.
```
netstat -a | grep bpcd
```
...gives me
```
tcp6       0      0 *:bpcd                  *:*                     LISTEN
```

How can I make it listen to tcp4 instead of tcp6?  I am really a novice in this business, so help is really appreciated.

The backup-software has an entry in ```
/etc/inetd.conf
``` like this:
```
bpcd stream tcp nowait.300 root /usr/openv/netbackup/bin/bpcd bpcd
```

Any ideas out there?

Espen

---

