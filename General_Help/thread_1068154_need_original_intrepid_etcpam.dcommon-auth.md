---
title: "need original intrepid /etc/pam.d/common-auth"
date: 2009-02-12
forum: General Help
---

### Post by blouz on 2009-02-12
Hello,

I am running Ubuntu 8.10 Intrepid.

I stupidly did not backup my /etc/pam.d/common-auth while performing some thinkfinger tests.
My file is all messed up and authentication is not working anymore :(

Could someone provide me the original Ubuntu intrepid /etc/pam.d/common-auth content ?

Thanks !!

---

### Post by kanikilu on 2009-02-12
I don't think I've modified mine from the distribution default, so...

```
#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
# As of pam 1.0.1-5, this file is managed by pam-auth-update by default.
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
auth	required			pam_permit.so
# and here are more per-package modules (the "Additional" block)
auth	optional	pam_ecryptfs.so unwrap
# end of pam-auth-update config

```

---

### Post by blouz on 2009-02-12
Many thanks kanikilu !

I just removed the ecryptfs line as i don't use this feature.

Regards.

---

