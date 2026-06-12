---
title: "Lightdm autologin : doesn't work the first time"
date: 2015-10-22
forum: Desktop Environments
---

### Post by stf2 on 2015-10-22
Hello,

I have a problem with autologin feature of lightdm : in summary, the autologin feature doesn't work, and still ask me to clic on a button "connect".

But here is the full explanation :
I'm in a context of customizing a Lubuntu livecd. I've created a new users, and I don't use the user created by Casper. (For any reason, casper fails to create the usual "lubuntu" user). I've made the "autologin" configuration in lightdm.conf, and put my user into the "nopasswdlogin" group.
During the boot, when lightdm is launched the first time, lightdm show a user selection with my user selected, and a simple button "connect" below ("se connecter" in french). It doesn't ask any password, but I still have to click on this button before being logged.
I clic on this button "connect". Then, after having being logged a first time, I log out the user. I arrive on the same page of lightdm, with my user selected and only the button "connect".
At this moment, I can go to a console mode (Alt-F1), and I stop lightdm, (/etc/init.d/lightdm stop), and I start it again (/etc/init.d/lightdm start).

And now, without having made any other configuration change, lightdm start and automatically log me in with my user.

Could you help me to avoid having to click on the button "connect" at the first login ?

Thank you,

---

### Post by deadflowr on 2015-10-22
What's the output for the lightdm.conf file?

---

### Post by stf2 on 2015-10-23
Hello,

Here is the content of my "lightdm.conf" file :

```
[SeatDefaults]
allow-guest=false
autologin-guest=false
autologin-user=tsv
autologin-user-timeout=0
autologin-session=lightdm-autologin
```


And here is the result, when the button appears (Autologin has failed actually) of lightdm.log :

```
[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.14.0, UID=0 PID=1106
[+0.00s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/20-lubuntu.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
[+0.00s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-myconfig.conf
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registered seat module xlocal
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Registered seat module unity
[+0.02s] DEBUG: Monitoring logind for seats
[+0.02s] DEBUG: New seat added from logind: seat0
[+0.02s] DEBUG: Loading properties from config section SeatDefaults
[+0.02s] DEBUG: Seat seat0: Starting
[+0.02s] DEBUG: Seat seat0: Creating user session
[+0.02s] DEBUG: Loading users from org.freedesktop.Accounts
[+0.02s] DEBUG: User /org/freedesktop/Accounts/User1000 added
[+0.05s] DEBUG: Seat seat0: Failed to find session configuration lubuntu
[+0.05s] DEBUG: Seat seat0: Can't find session 'lubuntu'
[+0.05s] DEBUG: Seat seat0: Creating greeter session
[+0.05s] DEBUG: Seat seat0: Creating display server of type x
[+0.07s] DEBUG: Deactivating Plymouth
[+0.09s] DEBUG: Using VT 7
[+0.09s] DEBUG: Seat seat0: Starting local X display on VT 7
[+0.09s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+0.09s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+0.09s] DEBUG: DisplayServer x-0: Launching X Server
[+0.09s] DEBUG: Launching process 1127: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.09s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+0.09s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.09s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.68s] DEBUG: Got signal 10 from process 1127
[+0.68s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+0.68s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+0.68s] DEBUG: Quitting Plymouth; retaining splash
[+0.71s] DEBUG: Seat seat0: Display server ready, starting session authentication
[+0.71s] DEBUG: Session pid=1206: Started with service 'lightdm-greeter', username 'lightdm'
[+0.74s] DEBUG: Session pid=1206: Authentication complete with return value 0: Success
[+0.74s] DEBUG: Seat seat0: Session authenticated, running command
[+0.74s] DEBUG: Session pid=1206: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/lightdm-gtk-greeter
[+0.74s] DEBUG: Creating shared data directory /var/lib/lightdm-data/lightdm
[+0.74s] DEBUG: Session pid=1206: Logging to /var/log/lightdm/x-0-greeter.log
[+0.78s] DEBUG: Activating VT 7
[+0.78s] DEBUG: Activating login1 session c1
[+0.78s] DEBUG: Seat seat0 changes active session to c1
[+0.78s] DEBUG: Session c1 is already active
[+0.96s] DEBUG: Session pid=1206: Greeter connected version=1.14.0 resettable=false
[+1.99s] DEBUG: Session pid=1206: Greeter start authentication for tsv
[+1.99s] DEBUG: Session pid=1256: Started with service 'lightdm', username 'tsv'
[+2.02s] DEBUG: Session pid=1256: Authentication complete with return value 0: Success
[+2.02s] DEBUG: Session pid=1206: Authenticate result for user tsv: Success
[+2.02s] DEBUG: Session pid=1206: User tsv authorized
[+20.32s] DEBUG: Seat seat0 changes active session to
[+27.23s] DEBUG: Seat seat0 changes active session to c2
```

Any idea where I could search ?

Note that I have also another file I should remove, but which is still there in /etc/lightdm/lightdm.conf.d/50-myconfig.conf :

```
[SeatDefaults]
autologin-user=tsv
user-session=lubuntu
autologin-user-timeout=0
autologin-user=tsv
```

---

### Post by deadflowr on 2015-10-23
Have you tried it with 
```
user-session=Lubuntu
```
seems to have a problem finding lubuntu.

---

### Post by stf2 on 2015-10-26
Hello,

Thank you so much. It is so obvious ! :D

I checked already that the "user-session" declared were existing in "var/share/xsession/" but I haven't seen that there were a mistake of capital letter : "lubuntu" instead of "Lubuntu".

Thank you again so much for your help. It works.

But the strange things which lead me to a wrong interpretation, is that the automatic login were working after a first connection.

---

