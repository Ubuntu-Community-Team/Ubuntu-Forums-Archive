---
title: "lightdm will not let domain user log in"
date: 2014-02-15
forum: Desktop Environments
---

### Post by yanqian on 2014-02-15
Hi, I am using Ubuntu 12.04, and config it authenticate with active directory domain following this document:
[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

The problem is that the domain user can not login via lightdm, but can login SSH successfully.

Here is the log in /var/log/auth.log (tempered with username and domain name only)

> ubuntu-01 lightdm: pam_krb5(lightdm:auth): user test_name authenticated as [email]test_name@EXAMPLE.CORP[/email]
ubuntu-01 lightdm: gkr-pam: error looking up user information
ubuntu-01 lightdm: pam_unix(lightdm:account): could not identify user (from getpwnam(test_name))

I have digged in the internet several days, but couldn't find the solution to this.
Does anyone have the same issue?

---

### Post by alf-emcom on 2014-04-10
Yes. I have exactly the same issue - using 13.10, 32 bit, desktop. It bugs the bejeezus out of me... Unfortunately, I have just as much luck as you finding a solution.

---

### Post by alf-emcom on 2014-04-10
And - now the problem is ... gone ??
I did a pam-auth-update and nothing seemed to happen, but following some other threads, I tailed -f the /var/log/lightdm/x-0-greeter.log, and when I tried to log in again it went OK. Probably just a delay in the effect of pam-auth-update.

---

