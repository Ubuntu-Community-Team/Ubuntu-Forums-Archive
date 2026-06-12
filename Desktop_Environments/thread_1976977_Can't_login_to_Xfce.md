---
title: "Can't login to Xfce"
date: 2012-05-09
forum: Desktop Environments
---

### Post by x1a4 on 2012-05-09
Hi,

Recently my laptop's battery died (while it was on) and since then I'm unable to login to Xfce.  When I try to log in it drops me back to the login screen.  I have NotIon installed and I can login to it just fine, as well as with the console.  Xorg logs show no error.

Thank you for your help.

EDIT:  This is on Xubuntu 12.04 (upgraded from 11.10) running on a ThinkPad X120e.

---

### Post by Toz on 2012-05-09
Check the ownership of the ~/.Xauthority and ~/.ICEauthority files (in your home directory). If they are not owned by you, change the ownership or delete them.

Otherwise, post back the contents of your ~/.xsession-errors file after an unsuccessful login attempt.

---

### Post by x1a4 on 2012-05-10
D'oh.  I forgot about those.  I deleted them and I can log in again. :)  Thanks.

---

