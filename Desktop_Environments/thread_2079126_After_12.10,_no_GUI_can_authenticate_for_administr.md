---
title: "After 12.10, no GUI can authenticate for administration, such as Software Center"
date: 2012-11-01
forum: Desktop Environments
---

### Post by mikecrowe on 2012-11-01
I upgraded to 12.10, and now I can't use Software Center or Network Administration.  It keeps giving me an authentication errors.  When I check /var/log/auth.log, I see:

```
    Oct 31 21:10:45 mike polkit-agent-helper-1[4665]: pam_unix(polkit-1:auth): authentication failure; logname= uid=1000 euid=0 tty= ruser=root rhost=  user=root
    Oct 31 21:10:51 mike polkit-agent-helper-1[4667]: pam_unix(polkit-1:auth): authentication failure; logname= uid=1000 euid=0 tty= ruser=root rhost=  user=root
```

I found a post which said to change my password, which I've done (both through the Ubuntu settings GUI tool, and through recovery mode).  No avail.

Any suggestions?

TIA
M

---

### Post by mikecrowe on 2012-11-09
OK, for whatever reason, ubuntu 12.10 needs a root password set.  You need to:
```
sudo passwd
```
to set your root password (who knew).  After that, things seem to work.

---

### Post by critin on 2012-11-09
> **mikecrowe said:**
> OK, for whatever reason, ubuntu 12.10 needs a root password set.  You need to:
```
sudo passwd
```to set your root password (who knew).  After that, things seem to work.

Something strange must have happened to your setup because I use 12.10 and my user login password runs everthing just like it always has. 

Do you now login with one pasword and do root admin stuff with another?  Do you still have to use sudo?

---

