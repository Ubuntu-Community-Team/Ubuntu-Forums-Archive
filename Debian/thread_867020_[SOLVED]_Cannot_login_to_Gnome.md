---
title: "[SOLVED] Cannot login to Gnome"
date: 2008-07-22
forum: Debian
---

### Post by x86i on 2008-07-22
I feel completely stupid for asking this, but:

I can log in with SSH with my user name. However, Gnome tells me that its an invalid user name/password.

I even created a new user to test with, and the auth log shows:

```
Jul 22 12:31:31 ATL3CLANDeb gdm[2878]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=  user=test
```

And the Syslog shows:

```
Jul 22 12:13:32 ATL3CLANDeb gdm[2878]: Couldn't authenticate user
Jul 22 12:13:47 ATL3CLANDeb gdm[2878]: Couldn't authenticate user
Jul 22 12:14:34 ATL3CLANDeb gdm[2878]: Couldn't authenticate user
Jul 22 12:15:53 ATL3CLANDeb gdm[2878]: Couldn't authenticate user

```
however, that user can log in via SSH without issue.


I know its probably something stupid I did, but I am lost. Please help:lolflag:

---

### Post by x86i on 2008-07-22
Solved.

Bad keyboard not typing password correctly. My bad.

---

