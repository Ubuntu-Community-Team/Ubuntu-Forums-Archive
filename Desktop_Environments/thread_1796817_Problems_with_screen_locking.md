---
title: "Problems with screen locking"
date: 2011-07-04
forum: Desktop Environments
---

### Post by mikerobinson on 2011-07-04
I'm having some problems with screen locking in Gnome.

- When the screen is locked, it doesn't authenticate any of the users. I have to select "switch user" and select the user from gdm in order to authenticate.

- For one of the users, the screen keeps locking after around 3 minutes of inactivity. Under the screensaver preferences it is set to 20 minutes and "lock screen when screensaver is active" is unchecked. However, it works for another user.

(Edit: It's a fresh install of 11.04.)

---

### Post by mikerobinson on 2011-07-04
I just tried it again and this is what is in my /var/log/auth.log:

> Jul  4 07:26:25 mike unix_chkpwd[2129]: check pass; user unknown
Jul  4 07:26:25 mike unix_chkpwd[2129]: password check failed for user (eric)
Jul  4 07:26:25 mike gnome-screensaver-dialog: pam_unix(gnome-screensaver:auth): authentication failure; logname= uid=1001 euid=1001 tty=:2.0 ruser= rhost=  user=eric
Jul  4 07:26:28 mike unix_chkpwd[2131]: check pass; user unknown

---

### Post by mikerobinson on 2011-07-05
Somehow my /etc/shadow got chowned to root:root instead of root:shadow. Setting the correct ownership fixed both problems.

---

