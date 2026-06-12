---
title: "Xscreensaver / PAM problem"
date: 2005-10-13
forum: Desktop Environments
---

### Post by d98_ama on 2005-10-13
Hi,

After upgrading from 5.04 to 5.10 I can no longer unlock my screensaver.
If I look in auth.log I can see entries like these:

Oct 13 20:48:28 localhost, unix_chkpwd[15937]: check pass; user unknown
Oct 13 20:48:28 localhost, xscreensaver: (pam_unix) authentication failure; logname= uid=1001 euid=1001 tty=:0.0 ruser= rhost=  user=anders
Oct 13 20:48:30 localhost, unix_chkpwd[15938]: check pass; user unknown
Oct 13 20:48:30 localhost, xscreensaver: (pam_unix) authentication failure; logname= uid=1001 euid=1001 tty=:0.0 ruser= rhost=  user=root
Oct 13 20:48:32 localhost, xscreensaver[15845]: FAILED LOGIN 1 ON DISPLAY ":20.0", FOR "anders"

Anybody knows why? Why does it say "check pass; user unknown"??

/Anders

---

### Post by d98_ama on 2005-10-13
It was a problem with my shadow file. It was:
-rw-------  1 root root 991 2005-10-12 20:34 /etc/shadow

and I changed it to:
-rw-r-----  1 root shadow 991 2005-10-12 20:34 /etc/shadow

Now lets just hope I didn't do anything stupid :)

---

