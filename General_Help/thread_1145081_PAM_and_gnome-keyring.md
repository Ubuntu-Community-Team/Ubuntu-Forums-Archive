---
title: "PAM and gnome-keyring"
date: 2009-05-01
forum: General Help
---

### Post by Mauler5858 on 2009-05-01
I am trying to setup a domain user so that his password at login will unlock the keyring by default.  I found a way to do it with PAM, and it will work for local users, just not domain users. Any clue as to why this is doing this.

> sudo apt-get install libpam-keyring

The next step is to actually make use of this PAM plug-in. Edit /etc/pam.d/gdm and add the following in the bottom:

auth optional pam_keyring.so try_first_pass
session optional pam_keyring.so

Log out and back in, and the Gnome keyring will be opened by your login!

---

