---
title: "Disable delay when incorrect password entered on login/sudo/gksudo"
date: 2009-06-02
forum: Desktop Environments
---

### Post by aml on 2009-06-02
Hi,

The delay caused by typing an incorrect password provides no valuable increase in security for me (no remote logon, complex passwords, single user able to logon, and all running on an encrypted partition).

Every now and again though - ironically when I'm in a hurry - I type my password or username wrong and have to wait at least two seconds before my OS allows me to try again. Every time this happens it annoys me a little bit more that I haven't been able to figure out how to disable it.

/etc/pam.d/login tantalisingly  suggests that I should add the 'nodelay' option to 'pam_unix' - does anyone know what this means and how to do it?

---

### Post by sisco311 on 2009-06-02
Edit the /etc/pam.d/common-auth file as follows.

```
...
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)
**auth    [success=1 default=ignore]      pam_unix.so nullok_secure nodelay**
# here's the fallback if no module succeeds
auth    requisite                       pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth    required                        pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config

```

---

