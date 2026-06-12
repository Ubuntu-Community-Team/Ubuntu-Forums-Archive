---
title: "Unity Freezes"
date: 2014-09-12
forum: Desktop Environments
---

### Post by KenF on 2014-09-12
Situation:

[LIST=1]
[*]Ubuntu 14.04
[*]Multiple Users Login (and switch user)
[*]After approximately 5 days of use, Unity Freezes.  Mouse moves but is useless.
[*]I can still go into a virtual term (e.g.  ctrl-alt-f1)
[/LIST]

"ps" and "top" do not show anything suscpicious:  No runaway processes, etc.  The only think odd is that in the lightdm log, there are two lines that are at about the right time for the freeze:

[+366404.93s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
[+366405.02s] DEBUG: User /org/freedesktop/Accounts/User1001 changed


Both uid 1000 and 1001 were logged in at the time, none of the other users were logged in.  I've searched to see if this is a known bug, but haven't found anything.

When it freezes up, I usually restart the whole machine in a virtualtty (reboots are 5sec and restarting lightdm seems to have more subsequent issues and kills the users desktop processes anyway).

Any advice/help?  Any more logfiles to look at?


p.s.  I also get some other logfile messages, but I believe these are coming from my switch to a vtty:
Sep 12 10:03:44 kenandlori kernel: [366556.209973] HDMI: ELD buf size is 0, force 128
Sep 12 10:03:44 kenandlori kernel: [366556.209995] HDMI: invalid ELD data byte 0

---

### Post by jorge8 on 2015-01-15
Did you find out what the problem was?  I'm having a similar problem.  I created a new user account "steam" (with UID 1001) and configured lightdm to launch openbox into this session.  Xorg is running, but openbox isn't.  Here's my "/var/log/lightdm/lightdm.log" file:


```
[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.10.3, UID=0 PID=1814
[+0.00s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/90-nvidia.conf
[+0.00s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registered seat module xlocal
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Registered seat module unity
[+0.00s] DEBUG: Registered seat module surfaceflinger
[+0.00s] DEBUG: Adding default seat
[+0.00s] DEBUG: Seat: Starting
[+0.00s] DEBUG: Seat: Creating user session
[+0.04s] DEBUG: Loading users from org.freedesktop.Accounts
[+0.04s] DEBUG: User /org/freedesktop/Accounts/User1001 added
[+0.05s] DEBUG: User /org/freedesktop/Accounts/User1000 added
[+0.06s] DEBUG: Seat: Creating display server of type x
[+0.06s] DEBUG: Deactivating Plymouth
[+0.08s] DEBUG: Using VT 7
[+0.08s] DEBUG: Seat: Starting local X display on VT 7
[+0.08s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+0.08s] DEBUG: DisplayServer x-0: Writing X server authority to /run/lightdm/root/:0
[+0.08s] DEBUG: DisplayServer x-0: Launching X Server
[+0.08s] DEBUG: Launching process 1846: /usr/bin/X -core :0 -seat seat0 -auth /run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.08s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+0.08s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.08s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+1.07s] DEBUG: Got signal 10 from process 1846
[+1.07s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+1.07s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+1.07s] DEBUG: Quitting Plymouth; retaining splash
[+1.09s] DEBUG: Launching process 1874: /sbin/prime-offload
[+1.09s] DEBUG: Process 1874 exited with return value 0
[+1.09s] DEBUG: Seat: Exit status of /sbin/prime-offload: 0
[+1.09s] DEBUG: Seat: Display server ready, starting session authentication
[+1.09s] DEBUG: Session pid=1883: Started with service 'lightdm-autologin', username 'steam'
[+1.12s] DEBUG: Session pid=1883: Authentication complete with return value 0: Success
[+1.12s] DEBUG: Seat: Session authenticated, running command
[+1.12s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+1.12s] DEBUG: Session pid=1883: Running command /etc/X11/Xsession /usr/bin/openbox-session
[+1.12s] DEBUG: Creating shared data directory /var/lib/lightdm-data/steam
[+1.12s] DEBUG: Session pid=1883: Logging to .xsession-errors
[+1.12s] DEBUG: Activating VT 7
[+1.12s] DEBUG: Activating login1 session c1
[+2.55s] DEBUG: User /org/freedesktop/Accounts/User1001 changed
[+2.55s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
[+3.73s] DEBUG: User /org/freedesktop/Accounts/User1001 changed
[+3.74s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
[+14.04s] DEBUG: User /org/freedesktop/Accounts/User1001 changed
[+14.05s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
```

---

### Post by KenF on 2015-01-19
Not really.  I'm now pretty sure it has to do with compiz freezing.  The following command seems to be the best way to clean things up:

sudo killall -KILL compiz

I wish you luck.

---

