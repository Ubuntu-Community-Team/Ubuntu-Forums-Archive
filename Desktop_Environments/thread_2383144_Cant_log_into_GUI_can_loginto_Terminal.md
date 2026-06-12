---
title: "Cant log into GUI can loginto Terminal"
date: 2018-01-21
forum: Desktop Environments
---

### Post by rsteinmetz70112 on 2018-01-21
On one of my machines when I try to log into to my old kernel I can't login it returns me to the GUI login screen.
If I change sessions I can log into a terminal session.
I have deleted .Xauthority with no change.
I have located a file which is created with the failed login attempt called .xsession-errors.
The contents of that files are below.

```
openConnection: connect: No such file or directory
cannot connect to brltty at :0
upstart: gnome-session (GNOME) main process (4716) terminated with status 1
upstart: logrotate main process (4468) killed by TERM signal
upstart: upstart-dbus-session-bridge main process (4639) terminated with status 1
upstart: bamfdaemon main process (4608) killed by TERM signal
upstart: Disconnected from notified D-Bus bus
```

Not sure what that means. I have some other problems with this machine as a result of problems with memory failing during an upgrade. I have solves most of those altheoug some still linger.

I can work using my current kernel and a 3rd backup but apt wants me to autoremove the third one leaving me with no working backup.

Ubuntu 16.04.3 LTS

---

