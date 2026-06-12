---
title: "unclean logout/can't log back in"
date: 2007-12-22
forum: Desktop Environments
---

### Post by linas on 2007-12-22
I'm having a problem with feisty, and now also with gutsy ...

I have a computer shared by 3 users (wife, kids), with frequent logouts/logins;
each has their own account, and so there are 4 to 8- logouts/logins a day.  Every 
week or two, there's a "unclean logout", for some unknown reason.

Symptoms: user can't log back in, system usually hangs with blank screen.
The three-finger ctrl+alt+backspace to kill and restart X11 doesn't fix it.
I can ssh in remotely,  as root, and  ps aux shows a number of processes
still running for the logged-out user. For example:


inudv    24382 99.4  6.5 167140 67820 ?        Rl   00:36 720:56 /usr/lib/firefox

inudv    24954  0.0  0.1   2900  1040 ?        Ss   00:40   0:00 dbus-daemon --fork --print-address 17 --print-pid 19 --session
inudv    24963  0.0  0.3   5160  3584 ?        SLs  00:40   0:00 /usr/bin/esd -terminate -nobeeps
inudv    24975  0.0  0.3   8728  3360 ?        S    00:40   0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
inudv    25161  0.0  0.0   2776   928 ?        Ss   00:41   0:00 dbus-daemon --fork --print-address 17 --print-pid 19 --session
inudv    25163  0.0  0.9  38304  9876 ?        Sl   00:41   0:00 /usr/lib/gnome-control-center/gnome-settings-daemon
inudv    25241  0.0  0.0   2776   932 ?        Ss   00:42   0:00 dbus-daemon --fork --print-address 17 --print-pid 19 --session
inudv    25243  0.0  0.9  38308  9880 ?        Sl   00:42   0:00 /usr/lib/gnome-control-center/gnome-settings-daemon
inudv    25345  0.0  0.0   2772   924 ?        Ss   00:44   0:00 dbus-daemon --fork --print-address 17 --print-pid 19 --session
inudv    25347  0.0  0.9  38308  9880 ?        Sl   00:44   0:00 /usr/lib/gnome-control-center/gnome-settings-daemon
inudv    25664  0.0  0.0   2772   928 ?        Ss   12:40   0:00 dbus-daemon --fork --print-address 17 --print-pid 19 --session
inudv    25666  0.1  0.9  38300  9876 ?        Sl   12:40   0:00 /usr/lib/gnome-control-center/gnome-settings-daemon

Notice that the start time was after midnight (00:36, 00:40, etc) and that firefox had been running full-tilt (720:56) for the last 12 hours. This despite the fact that the user had logged out of their X session. Not switch-user, but a full logout. I can kill -9 these by hand, but I sure don't like the fact that I have to rescue like this every so often. 

(We went to full-logout long ago, because switch-user wasn't sufficiently reliable.)

This has been going on for 6+months, under both feisty and now gutsy.

:confused:

---

### Post by Robdgreat on 2008-02-07
Bump.

I'm having essentially the same problem - frequent logins/logouts causing issues. Any help would be appreciated. TIA

---

