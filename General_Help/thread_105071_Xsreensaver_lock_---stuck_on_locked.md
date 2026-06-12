---
title: "Xsreensaver lock ---stuck on locked"
date: 2005-12-17
forum: General Help
---

### Post by tauruswho on 2005-12-17
I have spent a few days getting ubuntu (Kubuntu) set up just how I want it, great so far, but a small problem is that when the desktop sceensaver goes into lock seesion I can't get the session back as the password does not work, the only way out is to CTRL ALT Backspace....  This happens in Kde gnome and xfce4 and for other users as well.  Anyone got fix for this, must be something simple??????:) :)

---

### Post by tauruswho on 2005-12-18
Looked at /var/log/auth.log after checking users, seems to do with pam_unix stuff????. Have reinstalled libpam with no change. Still lost as to what is going on???

log file:---

Dec 18 20:40:30 who usermod[6867]: change user `mark' GID from `1000' to `1000'
Dec 18 20:40:30 who usermod[6867]: change user `mark' shell from `/bin/bash' to `/bin/bash'
Dec 18 20:40:30 who usermod[6867]: change user `mark' password
Dec 18 20:40:30 who usermod[6869]: change user `ntp' GID from `117' to `117'
Dec 18 20:40:30 who usermod[6869]: change user `ntp' shell from `/bin/false' to `/bin/false'
Dec 18 20:40:30 who usermod[6869]: change user `ntp' password
Dec 18 20:40:30 who usermod[6871]: change user `twat' GID from `1001' to `1001'
Dec 18 20:40:30 who usermod[6871]: change user `twat' shell from `/bin/bash' to `/bin/bash'
Dec 18 20:40:30 who usermod[6871]: change user `twat' password
Dec 18 20:40:30 who usermod[6873]: change user `kathy' GID from `1002' to `1002'
Dec 18 20:40:30 who usermod[6873]: change user `kathy' shell from `/bin/bash' to `/bin/bash'
Dec 18 20:40:30 who usermod[6873]: change user `kathy' password
Dec 18 20:40:30 who usermod[6875]: change user `laura' GID from `1003' to `1003'
Dec 18 20:40:30 who usermod[6875]: change user `laura' shell from `/bin/bash' to `/bin/bash'
Dec 18 20:40:30 who usermod[6875]: change user `laura' password
Dec 18 20:40:30 who usermod[6877]: change user `robert' GID from `1004' to `1004'
Dec 18 20:40:30 who usermod[6877]: change user `robert' shell from `/bin/bash' to `/bin/bash'
Dec 18 20:40:30 who usermod[6877]: change user `robert' password
Dec 18 20:40:30 who usermod[6879]: change user `emma' GID from `1005' to `1005'
Dec 18 20:40:30 who usermod[6879]: change user `emma' shell from `/bin/bash' to `/bin/bash'
Dec 18 20:40:30 who usermod[6879]: change user `emma' password
Dec 18 20:40:30 who usermod[6881]: change user `rachel' GID from `1006' to `1006'
Dec 18 20:40:30 who usermod[6881]: change user `rachel' shell from `/bin/bash' to `/bin/bash'
Dec 18 20:40:30 who usermod[6881]: change user `rachel' password
Dec 18 20:40:30 who usermod[6883]: change user `alex' GID from `1007' to `1007'
Dec 18 20:40:31 who usermod[6883]: change user `alex' shell from `/bin/bash' to `/bin/bash'
Dec 18 20:40:31 who usermod[6883]: change user `alex' password
Dec 18 20:40:31 who usermod[6885]: change user `minty' GID from `1008' to `1008'
Dec 18 20:40:31 who usermod[6885]: change user `minty' shell from `/bin/bash' to `/bin/bash'
Dec 18 20:40:31 who usermod[6885]: change user `minty' password
Dec 18 20:40:31 who usermod[6887]: change user `mince' GID from `1009' to `1009'
Dec 18 20:40:31 who usermod[6887]: change user `mince' shell from `/bin/bash' to `/bin/bash'
Dec 18 20:40:31 who usermod[6887]: change user `mince' password
Dec 18 20:40:31 who usermod[6889]: change user `mysql' GID from `118' to `118'
Dec 18 20:40:31 who usermod[6889]: change user `mysql' shell from `/bin/false' to `/bin/false'
Dec 18 20:40:31 who usermod[6889]: change user `mysql' password
Dec 18 20:40:31 who usermod[6891]: change user `clamav' GID from `119' to `119'
Dec 18 20:40:31 who usermod[6891]: change user `clamav' shell from `/bin/false' to `/bin/false'
Dec 18 20:40:31 who usermod[6891]: change user `clamav' password
Dec 18 20:40:31 who usermod[6893]: change user `ftp' GID from `65534' to `65534'
Dec 18 20:40:31 who usermod[6893]: change user `ftp' shell from `/bin/false' to `/bin/false'
Dec 18 20:40:31 who usermod[6893]: change user `ftp' password
Dec 18 20:40:31 who usermod[6895]: change user `userftp' GID from `100' to `100'
Dec 18 20:40:31 who usermod[6895]: change user `userftp' shell from `/bin/false' to `/bin/false'
Dec 18 20:40:31 who usermod[6895]: change user `userftp' password
Dec 18 20:41:17 who gdm[5246]: (pam_unix) session closed for user root
Dec 18 20:42:12 who unix_chkpwd[7147]: check pass; user unknown
Dec 18 20:42:12 who kcheckpass: (pam_unix) authentication failure; logname= uid=1000 euid=1000 tty=:5 ruser= rhost=  user=mark
Dec 18 20:42:12 who kcheckpass[7146]: Authentication failure for mark (invoked by uid 1000)
Dec 18 20:42:37 who gdm[5246]: (pam_unix) session opened for user root by (uid=0)

:confused: :rolleyes:

---

### Post by Txukie on 2005-12-19
Bypass this already reported bug by
sudo chmod 4755 /usr/bin/kcheckpass

---

### Post by tauruswho on 2005-12-19
Thank you, that did the trick...:) :)

---

### Post by Copter on 2006-04-12
had to use this trick again after apt-get upgrade of kde 3.5.0 to kde 3.5.2

thanks!

copter :]

---

### Post by Flapidouille on 2006-05-26
[QUOTE=Txukie]Bypass this already reported bug by
sudo chmod 4755 /usr/bin/kcheckpass[/QUOTE]
[COLOR="DarkRed"]Hello ! I have the same problem, although I did not enable the "lock screen" option.Sometimes only :confused: 
As I am new to Ubuntu I would like confirmation before I do anything wrong: could I use this trick in that case, and does it work with Dapper ? :) Thanks to whoever can help.[/COLOR]

---

