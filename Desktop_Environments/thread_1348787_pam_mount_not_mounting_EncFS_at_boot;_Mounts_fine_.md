---
title: "pam_mount not mounting EncFS at boot; Mounts fine manually"
date: 2009-12-07
forum: Desktop Environments
---

### Post by vik.vaughn on 2009-12-07
I have a shared NFS folder that is mounting correctly on login, and I have an EncFS folder that mounts to that folder fine manually (if I type "su - $USER" I see it mount.) For some reason, when I bootup my computer, the NFS folder mounts, but the EncFS mount doesn't happen. I've double-checked my /etc/security/pam_mount.conf.xml and everything seems to be right. It almost seems like Ubuntu isn't even trying to use the pam_mount module on boot, or like it doesn't even know it's got an EncFS share that's supposed to mount.

I'm kind of at a loss as to where to even start troubleshooting this issue. If anyone could offer any help that would be great. I've tried grepping the syslog and messages files but nothing comes up under "pam"

---

### Post by vik.vaughn on 2009-12-07
Also, if I login via the command line (by hitting ctrl+alt+F1) once I've booted into gnome, all of the pam_mount debugging info scrolls as soon as I login, and the encfs mount works.

So it looks like the automatic mounting is only attempting during the command line session and not during the gdm session.

I checked the /etc/pam.d/gdm file and it has "@include common-auth" which if I understand correctly is kind of like a link to the /etc/pam.d/common-auth file. My common-auth file has "auth optional pam_mount.so" in it, so that should be used when booting into gdm, right?

here is the entire common-auth that is referenced by gdm:

```
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)
auth	[success=1 default=ignore]	pam_unix.so nullok_secure
# here's the fallback if no module succeeds
auth	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth	requisite			pam_permit.so
# and here are more per-package modules (the "Additional" block)
auth	optional	pam_mount.so 
# end of pam-auth-update config
```

---

### Post by vik.vaughn on 2009-12-08
So I have determined that logging in using "su" automatically mounts the EncFS folder, but logging into Gnome using the normal bootup/gui login does not work.

I checked and there is a file for each of those login scenarios in /etc/pam.d/ but I didn't want to go through changing them blindly for fear of locking myself out of my system.

Here is a comparison of the two. Su works, gdm-autologin doesn't.

su
```
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
auth    required        pam_permit.so
@include common-account
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close
session required        pam_limits.so
@include common-session
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open
@include common-password
```

gdm-autologin
```
auth       sufficient pam_rootok.so
session       required   pam_env.so readenv=1
session       required   pam_env.so readenv=1 envfile=/etc/default/locale
session    optional   pam_mail.so nopen
@include common-auth
@include common-account
@include common-session
```

---

