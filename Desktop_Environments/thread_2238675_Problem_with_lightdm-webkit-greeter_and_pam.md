---
title: "Problem with lightdm-webkit-greeter and pam"
date: 2014-08-09
forum: Desktop Environments
---

### Post by SeaKing on 2014-08-09
Hey,
currently I'm trying to create an own lightdm-webkit-greeter for Lubuntu 14.04, but login with the right credentials fails:

lightdm.log
```

[+357.23s] DEBUG: Session pid=1675: Greeter start authentication for seaking
[+357.23s] DEBUG: Session pid=1913: Started with service 'lightdm', username 'seaking'
[+357.25s] DEBUG: Session pid=1913: Got 1 message(s) from PAM
[+357.25s] DEBUG: Session pid=1675: Prompt greeter with 1 message(s)
**[+357.26s] DEBUG: Session pid=1913: Authentication complete with return value 7: Authentication failure**
[+357.26s] DEBUG: Session pid=1675: Authenticate result for user seaking: Authentication failure
[+357.26s] DEBUG: Session pid=1913: Exited with return value 1
[+357.26s] DEBUG: Seat: Session stopped

```

auth.log
```

Aug  9 15:26:20 sk91-vm01-a lightdm: PAM unable to dlopen(pam_gnome_keyring.so): /lib/security/pam_gnome_keyring.so: cannot open shared object file: No such file or directory
Aug  9 15:26:20 sk91-vm01-a lightdm: PAM adding faulty module: pam_gnome_keyring.so
Aug  9 15:26:20 sk91-vm01-a lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Aug  9 15:26:20 sk91-vm01-a lightdm: PAM adding faulty module: pam_kwallet.so
Aug  9 15:26:20 sk91-vm01-a lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "seaking"
Aug  9 15:26:20 sk91-vm01-a lightdm: pam_unix(lightdm:auth): conversation failed
Aug  9 15:26:20 sk91-vm01-a lightdm: pam_unix(lightdm:auth): auth could not identify password for [seaking]

```

/etc/pam/lightdm
```

#%PAM-1.0
auth    requisite       pam_nologin.so
auth    sufficient      pam_succeed_if.so user ingroup nopasswdlogin
@include common-auth
auth    optional        pam_gnome_keyring.so
auth    optional        pam_kwallet.so
@include common-account
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close
session required        pam_limits.so
@include common-session
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open
session optional        pam_gnome_keyring.so auto_start
session optional        pam_kwallet.so auto_start
session required        pam_env.so readenv=1
session required        pam_env.so readenv=1 user_readenv=1 envfile=/etc/default/locale

```

also removing .Xauthority from the users home changed nothing.

If I use the lightdm-gtk-greeter it all works fine. Any ideas?

---

