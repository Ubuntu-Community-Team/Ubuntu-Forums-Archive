---
title: "Failure to connect to dbus on login"
date: 2013-01-14
forum: Desktop Environments
---

### Post by jtappin on 2013-01-14
On a system running Kubuntu 12.04 (with xubuntu desktop also installed); I frequently have a problem when logging in that KDE goes through all the various stages shown in the login monitor, and then hangs up. Also Xfce4 frequently fails to log in with error mesages about failed to connect to the dbus server.

Starting X from the console (with a .xinitrc file containing just one line
```
startkde
```
the final error message suggested running:
```
export $(dbus-launch)
```

(Sorry I don't have all the error messages as when I tried to run startx with the outputs redirected it worked properly--as best I can tell it's randon whether things start properly or not with a probability of a successful login rather below 0.5).

This is the current output of looking for dbus processes.
```
7 s >> ps -ef | grep dbus
102        958     1  0 13:21 ?        00:00:01 dbus-daemon --system --fork --activation=upstart
root      1180     1  0 13:21 ?        00:00:00 ypbind -no-dbus
jtappin   4482     1  0 13:36 ?        00:00:00 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
jtappin   4528     1  0 13:37 ?        00:00:00 //bin/dbus-daemon --fork --print-pid 4 --print-address 6 --session
jtappin   4712     1  0 13:40 ?        00:00:00 //bin/dbus-daemon --fork --print-pid 4 --print-address 6 --session
jtappin   4719     1  0 13:40 ?        00:00:00 //bin/dbus-daemon --fork --print-pid 4 --print-address 6 --session
jtappin   4933     1  0 13:44 ?        00:00:00 //bin/dbus-daemon --fork --print-pid 4 --print-address 6 --session
jtappin   5199     1  0 13:49 tty1     00:00:00 dbus-launch --sh-syntax --exit-with-session
jtappin   5200     1  0 13:49 ?        00:00:00 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
jtappin  12317 12147  0 14:37 pts/25   00:00:00 grep dbus

```
(I rather think that the dbus-daemon processes with PIDs in the 4000's were from my attempts to use dbus-launch.)

Does anybody have any suggestions of what to look for next time it starts playing up?

Also is the fact that usernames are handled via NIS and /home is nfs mounted likely to have any bearing on the problem?

---

