---
title: "Corrupt hosts file and gethostbyname() error preventing file modification"
date: 2006-09-09
forum: Desktop Environments
---

### Post by eschreib on 2006-09-09
Greetings, am unable to run any programs a 'root':

sudo *'anything'* yields:
sudo: unable to lookup 'mymachine' via gethostbyname()

so, I tried booting in w/ alt-ctrl-f1 also to no avail with above, or in tring to edit /ect/hosts with vi:

sudo vi  /ect/hosts
sudo: unable to lookup 'mymachine' via gethostbyname()


vi  /ect/hosts

:w  yields 
E45: 'readonly' option is set (add ! to override)
:w! yields
"hosts"' E212:Cant open file for writing


ping localhost yields:
unknown host localhost



Diagnostic files :


# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

---

### Post by croak77 on 2006-09-09
Well you can boot into recovery mode from grub or use the live-cd and mount your root partition. You need to make sure /etc/hosts and /etc/hostname have the same hostname. Did you change anyone of those two files?

---

### Post by Junx on 2006-09-09
> **croak77 said:**
> Well you can boot into recovery mode from grub or use the live-cd and mount your root partition. You need to make sure /etc/hosts and /etc/hostname have the same hosttname. Did you change anyone of those two files?
Yeah, if you want to make some changes that require root and you can't use sudo, boot into recover mode (aka single-user mode), mess around with /etc/hostname and whatnot, Ctrl+D to log out and continue booting normally.

---

