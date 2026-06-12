---
title: "gnome-screensaver does not unlock with CommonAccessCard"
date: 2009-06-02
forum: Desktop Environments
---

### Post by mbucknam on 2009-06-02
I followed the directions here:

[https://help.ubuntu.com/community/CommonAccessCard](https://help.ubuntu.com/community/CommonAccessCard)

to configure CAC login and gnome-screensaver.  This worked for me fine in 8.0.4 but I'm having a problem in 9.0.4

Logging in works fine but when I activate the screensaver, it first asks for smartcard (CAC) pin as expected but then also asks for my password.  It used to just unlock.

/etc/pam.d/gnome-screensaver:

auth 	sufficient    pam_pkcs11.so
@include common-auth
auth optional pam_gnome_keyring.so

---

