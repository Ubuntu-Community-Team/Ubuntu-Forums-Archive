---
title: "software Installation issue"
date: 2005-12-28
forum: General Help
---

### Post by faisalK on 2005-12-28
hi 

every time I try to install a software I get the following message:

Fetched 414kB in 6s (64.9kB/s)
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory



what is this

---

### Post by shin on 2005-12-28
Try
sudo dpkg-reconfigure locales
and generate locales you need.

If it won't work, check
[http://ubuntuforums.org/showthread.php?t=108442](http://ubuntuforums.org/showthread.php?t=108442)

It is a dapper thread but problem is the same.

---

