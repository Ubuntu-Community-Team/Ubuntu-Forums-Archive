---
title: "rkhunter trouble"
date: 2009-04-20
forum: General Help
---

### Post by standingchair on 2009-04-20
Hello Ubuntu Forums,
I'm running rkhunter version 1.3.4.
I'm experiencing false positive on files like /bin/which and the like. 
I've tried the command:

rkhunter --propupd

As well as:

rkhunter --propupd /bin/which

(for that particular file)

To update my database, but to no effect. Also in  /etc/rkhunter.conf
these files are supposedly whitelisted.

#
# Allow the specified commands to be scripts.
# One command per line (use multiple SCRIPTWHITELIST lines).
#
SCRIPTWHITELIST=/bin/egrep
SCRIPTWHITELIST=/bin/fgrep
SCRIPTWHITELIST=/bin/which
SCRIPTWHITELIST=/usr/bin/groups
SCRIPTWHITELIST=/usr/bin/ldd
SCRIPTWHITELIST=/usr/bin/lwp-request
SCRIPTWHITELIST=/usr/sbin/adduser
SCRIPTWHITELIST=/usr/sbin/prelink


Can anyone explain how to get this straightened out and accurate?
Please and thank you.
J

---

