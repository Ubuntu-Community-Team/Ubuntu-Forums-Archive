---
title: "gnome setting ACLs?"
date: 2010-10-30
forum: Desktop Environments
---

### Post by tgates81 on 2010-10-30
It appears after logging in to a gnome session ACLs are being set on devices for the user logging in, specifically the CDROM device. This is a problem for me because I don't want all my users to have free rein on burning sensitive data to CD's and DVD's.
I've submitted a bug about it [here]("https://bugs.launchpad.net/ubuntu/+bug/667338") but was told it was a done by design but we still don't know for sure where it is coming from or how to stop it. Does anyone here familiar with this process or how to stop it from happening?

Thanks,
    Tyler

---

### Post by tgates81 on 2010-11-07
Turns out udev was the culprit, not GNOME. /lib/udev/rules.d/70-acl.rules has a line like this:
```
SUBSYSTEM=="block", ENV{ID_CDROM}=="1", ENV{ACL_MANAGE}="1"

```I created my own rule and threw it in /etc/udev/rules.d/ which disabled the ACL_MANAGE variable:
```
SUBSYSTEM=="block", ENV{ID_CDROM}=="1", ENV{ACL_MANAGE}="0"

```Rebooted and all was well.

---

