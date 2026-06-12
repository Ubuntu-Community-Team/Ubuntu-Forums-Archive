---
title: "pam_unix(gdm-password:auth): conversation failed"
date: 2015-09-15
forum: Desktop Environments
---

### Post by persio on 2015-09-15
Since yesterday when I try to log in, I have to make several attempts to achieve it. I enter my password at the login screen and for a couple of times nothing happens, until it suddenly works. This is my log:

```
$ journalctl -e -u gdm

sep 15 16:29:14 r2 gdm[1090]: Failed to give slave programs access to the display. Trying to proceed.
sep 15 16:29:14 r2 gdm-launch-environment][6613]: pam_unix(gdm-launch-environment:session): session opened for user gdm by (uid=0)
sep 15 16:29:17 r2 gdm-password][6735]: pam_succeed_if(gdm-password:auth): requirement "user ingroup nopasswdlogin" not met by user "persio"
sep 15 16:29:20 r2 gdm-password][6735]: pam_unix(gdm-password:auth): conversation failed
sep 15 16:29:20 r2 gdm-password][6735]: pam_unix(gdm-password:auth): auth could not identify password for [persio]
sep 15 16:29:21 r2 gdm-password][6762]: pam_succeed_if(gdm-password:auth): requirement "user ingroup nopasswdlogin" not met by user "persio"
sep 15 16:29:22 r2 gdm-password][6762]: pam_ecryptfs: pam_sm_authenticate: /home/persio is already mounted
sep 15 16:29:22 r2 gdm-password][6762]: pam_unix(gdm-password:session): session opened for user persio by (unknown)(uid=0)
```
I'm running Ubuntu GNOME 15.04.

---

### Post by persio on 2015-09-18
anyone?

---

