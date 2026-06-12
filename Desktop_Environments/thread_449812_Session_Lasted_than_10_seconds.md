---
title: "Session Lasted than 10 seconds"
date: 2007-05-20
forum: Desktop Environments
---

### Post by Radical on 2007-05-20
I have this problem:




/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "emo"
/etc/gdm/Xsession: Beginning session setup...
sh: Syntax error: "(" unexpected


Post this:  
[http://ubuntuforums.org/showthread.php?t=28374](http://ubuntuforums.org/showthread.php?t=28374)

---

### Post by taurus on 2007-05-20
To make sure you don't run out of disk space, press <Ctrl><Alt>F2 and log in with your username and password.  Then, post the output of this command from a prompt.

```
df -h
```

---

### Post by kickaha on 2007-05-20
Generally, when I've encountered a 'session lasted less than 10 seconds' error message, it meant that /tmp was not world writeable, or that one of the *-<username> session files in /tmp was not over-writable.

Check for '777' permissions on /tmp, and for existing session files for your username.

Did you happen to change the UID of your user account? If so, you no longer own those session files, and they will not be over-writable or usable by your new UID.

I would cast around for permissions problems if I saw that message.

Chaers, and good luck.

---

### Post by Radical on 2007-05-22
> **taurus said:**
> To make sure you don't run out of disk space, press <Ctrl><Alt>F2 and log in with your username and password.  Then, post the output of this command from a prompt.

```
df -h
```

It's ok... Not full!

---

### Post by Radical on 2007-05-22
> **kickaha said:**
> Generally, when I've encountered a 'session lasted less than 10 seconds' error message, it meant that /tmp was not world writeable, or that one of the *-<username> session files in /tmp was not over-writable.

Check for '777' permissions on /tmp, and for existing session files for your username.

Did you happen to change the UID of your user account? If so, you no longer own those session files, and they will not be over-writable or usable by your new UID.

I would cast around for permissions problems if I saw that message.

Chaers, and good luck.


Doesn't change! :(

---

