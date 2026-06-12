---
title: "change password requirements"
date: 2009-03-14
forum: General Help
---

### Post by tone33 on 2009-03-14
How can I change the minimu requirements for the passwords in ubuntu?  I looked in /etc/pam.d/common-password, but do not see any parameters related to password length.  I am interested in having passwords shorter than 6 characters and no alpha-numeric requirements.

---

### Post by dcstar on 2009-03-15
> **tone33 said:**
> How can I change the minimu requirements for the passwords in ubuntu?  I looked in **/etc/pam.d/common-password**, but do not see any parameters related to password length.  I am interested in having passwords shorter than 6 characters and no alpha-numeric requirements.

From that file:

```
# You can also use the "min" option to enforce the length of the new
# password.
#
```

---

### Post by tone33 on 2009-03-15
hmm....not seeing that in my file.  here's what i got from a fresh install of Ubunutu 8.10:
```
#
# /etc/pam.d/common-password - password-related modules common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of modules that define the services to be
# used to change user passwords.  The default is pam_unix.

# Explanation of pam_unix options:
#
# The "sha512" option enables salted SHA512 passwords.  Without this option,
# the default is Unix crypt.  Prior releases used the option "md5".
#
# The "obscure" option replaces the old `OBSCURE_CHECKS_ENAB' option in
# login.defs.
#
# See the pam_unix manpage for other options.

# As of pam 1.0.1-5, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)
password	[success=1 default=ignore]	pam_unix.so obscure sha512
# here's the fallback if no module succeeds
password	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
password	required			pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config
```

---

