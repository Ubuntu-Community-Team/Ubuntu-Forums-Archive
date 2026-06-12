---
title: "GMailFS in Dapper"
date: 2006-09-18
forum: Desktop Environments
---

### Post by acascianelli on 2006-09-18
I'm trying to get GMailFS up and running on Ubuntu 6.06 and I get the following error...

Traceback (most recent call last):
  File "/usr/bin/mount.gmailfs", line 153, in ?
    pyfile, mountpoint, odata, useEncfs = parseCommandLineArgs(sys.argv[1:])
  File "/usr/bin/mount.gmailfs", line 66, in parseCommandLineArgs
    log.error("file %s doesn't exist, or is not a file" % pyfile)
NameError: global name 'log' is not defined

...I know GMailFS has been broken in Ubuntu for a long time now but does anybody know of a workaround or anything?

---

### Post by adamnmcc on 2006-11-21
if GmailFS doesn't work in Ubuntu, why is it in the apt-repositories?

---

