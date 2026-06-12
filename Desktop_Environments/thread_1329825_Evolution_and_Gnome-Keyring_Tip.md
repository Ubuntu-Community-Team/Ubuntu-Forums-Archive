---
title: "Evolution and Gnome-Keyring Tip"
date: 2009-11-17
forum: Desktop Environments
---

### Post by drumz on 2009-11-17
I switched to using the KDM login manager from GDM and as a result Evolution would prompt me for the Gnome keyring password which was annoying, doing some research online I figured out how to allow KDM to automatically start the gnome-keyring-manager just like GDM does.

Edit ```
sudo vi /etc/pam.d/kdm
``` so it looks like this (don't forget to make a backup first!):

```

#
# /etc/pam.d/kdm - specify the PAM behaviour of kdm
#
auth       required     pam_nologin.so
auth       required     pam_env.so readenv=1
auth       required     pam_env.so readenv=1 envfile=/etc/default/locale
@include common-auth
auth       optional     pam_gnome_keyring.so
session    required     pam_limits.so
@include common-account
@include common-password
@include common-session
session    optional     pam_gnome_keyring.so auto_start
```

Basically it's the same as the original file plus these two additional ones:

```
...
auth       optional     pam_gnome_keyring.so
...
session    optional     pam_gnome_keyring.so auto_start
```

Once that's done you can logout/restart and when you log back in Evolution won't prompt you for the gnome-keyring-manager password anymore (as long as it's the same as your login password).

Hopefully this will help someone else (or myself in the future when I forget how I did this ;-) )

---

### Post by pjssilva on 2011-12-14
Thanks!

I am using kdm to get a proper multiseat setup as lightdm is broken for multiseat now. This tip helped a lot.

---

