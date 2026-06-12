---
title: "xdm and pam_mkhomedir"
date: 2010-01-28
forum: Desktop Environments
---

### Post by royal_navy on 2010-01-28
Hello,
I have a problem which appears to be somehow related to xdm itself. It looks like when i use ldap authentication with pam_mkhomedir xdm doesn't login the user if the home directory doesn't exists.  (when user has the home directory everything looks and works perfectly fine). Any ideas how to solve this issue ?

Please find below the pam.d configs:
####
#
# /etc/pam.d/common-session - session-related modules common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of modules that define tasks to be performed
# at the start and end of sessions of *any* kind (both interactive and
# non-interactive).
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)
session	[default=1]			pam_permit.so
# here's the fallback if no module succeeds
session	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
session	required			pam_permit.so
# and here are more per-package modules (the "Additional" block)
session	required	pam_unix.so 
session required	pam_mkhomedir.so skel=/etc/skel/ umask=0022
session	optional			pam_ldap.so 
session	optional			pam_ck_connector.so nox11
####
# $Id: xdm.pam 189 2005-06-11 00:04:27Z branden $

@include pam-ssh-auth
@include common-auth
@include common-account
@include common-session
@include pam-ssh-session
@include common-password

auth		requisite	pam_nologin.so
auth		required	pam_env.so
auth		required	pam_env.so envfile=/etc/default/locale
session		required	pam_limits.so

---

### Post by Lorens on 2011-11-15
I have the same problem. Did you solved that?

---

