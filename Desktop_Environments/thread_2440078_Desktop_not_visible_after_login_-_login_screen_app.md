---
title: "Desktop not visible after login - login screen appears dead"
date: 2020-04-05
forum: Desktop Environments
---

### Post by j4nd3r53n on 2020-04-05
I'm using Ubuntu 18.04 with KDE on an HP Probook, and it has been working fine for 6 months. It seems, after an upgrade last week, I can no longer log in - or rather, it is as if I log in successfully, but I never get to see the desktop, and the login screen seems to be completely unresponsive, except that I can use CTL+ALT+F2 to get to a console. I can log in on the console and over ssh - when I log in as root over ssh, I initially see no processes belonging to my desktop user, then after I enter the correct password on the login screen:

```

# ps -ef | grep jan
jan.and+  1445     1  0 17:02 ?        00:00:00 /lib/systemd/systemd --user
jan.and+  1446  1445  0 17:02 ?        00:00:00 (sd-pam)
jan.and+  1457  1445  0 17:02 ?        00:00:00 /usr/bin/ssh-agent -D -a /run/user/1000/ssh-agent.socket
jan.and+  1459     1  0 17:02 ?        00:00:00 /usr/bin/kwalletd --pam-login 15 3 --nofork
jan.and+  1461     1  0 17:02 ?        00:00:00 /usr/bin/kwalletd5 --pam-login 15 3
jan.and+  1489     1  6 17:02 ?        00:00:00 /usr/bin/fcitx
jan.and+  1492  1445  0 17:02 ?        00:00:00 /usr/bin/dbus-daemon --session --address=systemd: --nofork --nopidfile --systemd-activation --syslog-only
jan.and+  1503     1  0 17:02 ?        00:00:00 /usr/bin/dbus-daemon --syslog --fork --print-pid 5 --print-address 15 --config-file /usr/share/fcitx/dbus/daemon.conf
jan.and+  1512     1  0 17:02 ?        00:00:00 /usr/bin/fcitx-dbus-watcher unix:abstract=/tmp/dbus-ZKmgfdU02T,guid=b5949af288fdb15ad04451685e8a012d 1503
jan.and+  1526  1492  0 17:02 ?        00:00:00 /usr/bin/dbus-daemon --session --address=systemd: --nofork --nopidfile --systemd-activation --syslog-only
jan.and+  1527  1526  0 17:02 ?        00:00:00 /usr/bin/plasma_waitforname org.freedesktop.Notifications

```

I need this laptop for my work, now that have to work from home during the corona crisis. Can anybody help?

---

### Post by lvm on 2020-04-06
Check ~/.xsession-errors. Your issue might be similar to the one discussed in this tread [https://ubuntuforums.org/showthread.php?t=2440110](https://ubuntuforums.org/showthread.php?t=2440110) - no magic answer yet, but I'd give the same advice: try rolling back the upgrades.

---

