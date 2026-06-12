---
title: "udisks automount (no login manager, just startx)"
date: 2012-06-21
forum: Desktop Environments
---

### Post by lo.j on 2012-06-21
hi all.

**ubuntu-server + kde-plasma-desktop** here, and i'm not able to automount an usb, i got:```
$ udisks --mount /dev/sdh1
Mount failed: Not Authorized
```

i'm posting here because all of my searches were useless.


here some useful outputs.

packages installed:```
consolekit
libpolkit-agent-1-0
libpolkit-backend-1-0
libpolkit-gobject-1-0
libpolkit-qt-1-1
policykit-1
polkit-kde-1
```

packages i tried to install (that did not solve anyway):```
gvfs
policykit-1-gnome
policykit-desktop-privileges
```

.xinitrc i tried to set (a line at a time, alternately):```
exec startkde
exec ck-launch-session startkde
exec ck-launch-session dbus-launch startkde
exec ck-launch-session dbus-launch --exit-with-session startkde

```

ck-list-sessions output (never chnaged, despite of all my attempts):```
unix-user = '1000'
realname = '(null)'
seat = 'Seat4'
session-type = ''
active = FALSE
x11-display = ':0'
x11-display-device = '/dev/tty8'
display-device = '/dev/tty1'
remote-host-name = ''
is-local = FALSE
on-since = '2012-06-21T18:57:30.878689Z'
login-session-id = '4294967295'
```

please, just ask for more outputs and thanks very much for any suggestion!

---

### Post by lo.j on 2012-06-23
i found the following workaround:```
$ cat /etc/polkit-1/localauthority/50-local.d/custom.pkla
[automount]
Identity=unix-group:sudo
Action=org.freedesktop.udisks.filesystem-*
ResultAny=yes
```
(my user is in the sudo group)

i'm calling it a workaround because of the **ResultAny=yes** line.
since i'm not able to have consolekit open an active session, i need to grant udisks to all sessions, active and not.
as you can understand, this is not a proper settings. i'd like to open as few vulnerabilities as i can.

i attach my startx (exec ck-launch-session dbus-launch --exit-with-session startkde) log.

i'm looking the web since days now, i'm still stuck here.
any help please?

thanks.

---

### Post by digitalnome on 2012-09-13
Many thanks

I have had the same issue 

[http://ubuntuforums.org/showthread.php?t=2053985](http://ubuntuforums.org/showthread.php?t=2053985)

I followed your advice however, I created and used a group called 'storage',  adding users to it. 

Still a little confused to how gdm/xdm/lightdm/SLiM/etc work without these settings and the implications of the above in terms of overall security on the box.

---

