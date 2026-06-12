---
title: "Can't login with correct password"
date: 2009-03-26
forum: General Help
---

### Post by jobbesat on 2009-03-26
Everything started when I edit the file /etc/pam.d/gdm adding the line
@include common-pamkeyring
to unlock the keyring

When I rebooted I could not login with my usual password.
So I tried to boot in recovery mode using bash shell as root to edit the file again deleting that line, but nothing, the problem was still there.
So, using live cd, I used the shell as root to browse into my home directory and delete the file:
.gnome2/keyrings/default.keyring
this file was not there, there was only the file
.gnome2/keyrings/login.keyring
and I deleted it.

Now the problem is still there and here's the strange fact: when I type atlogin my usual user/pass combo, there's a little popup window which claims "Authentication failed", while if I type my user with another wrong password, the same login window shows, as it should be, that user or pass are wrong, etc. etc.

Is there a "painless" way to solve the problem or I really have to reinstall from scratch?

---

