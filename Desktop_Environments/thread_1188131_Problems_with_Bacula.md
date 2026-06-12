---
title: "Problems with Bacula"
date: 2009-06-15
forum: Desktop Environments
---

### Post by Teledesign on 2009-06-15
I am trying to get Bacula working on my Ubuntu 9.04 Desktop machine.

Thus far I have had the following problems:

1) The Menu entry for "Bacula Administration Tool" in the GNU "system tools menu" points at /usr/sbin/bat

However the file (from your package) has been installed at:

usr/bin/bat

2) When running the above from the GNU menu, it needs to be run as root. But the menu has not be configured correctly.

3) The permissions on config file for the monitor program are not set correctly.

So far I have managed to fix the above - but am starting to loose confidence.

Regards

Andrew

---

### Post by mkalen on 2009-06-16
> **Teledesign said:**
> 
1) The Menu entry for "Bacula Administration Tool" in the GNU "system tools menu" points at /usr/sbin/bat

However the file (from your package) has been installed at:

usr/bin/bat

I just installed bacula-director-qt and hit the same problem as you did. I have filed a bug report for this:
[Bug #387778]("https://bugs.launchpad.net/ubuntu/+source/bacula/+bug/387778")

> **Teledesign said:**
> 
2) When running the above from the GNU menu, it needs to be run as root. But the menu has not be configured correctly.


My bat.conf got the following permissions on install:
```
-rw-r----- 1 root bacula 180 2009-06-16 10:16 /etc/bacula/bat.conf
```

This means I can use BAT if my user belongs to the bacula group:
```
sudo adduser martin bacula
```

You need to logout/login or su to your own user for this to take effect. Use the "groups" command to check.

> **Teledesign said:**
> 
3) The permissions on config file for the monitor program are not set correctly.


Do you mean /etc/bacula/tray-monitor.conf? For me it got the same permissions as all other config files (rw for root, r for bacula group).

I have tested the Bacula 2.4.4-1ubuntu5 packages under Kubuntu 9.04.

Regards,
 Martin

---

