---
title: "LightDM - Cannot autologin when X crashes"
date: 2014-11-23
forum: Desktop Environments
---

### Post by McArthor_Lee on 2014-11-23
hi all,


I find that LightDM cannot autologin my user when X crashes or when I kill X process, even if I configure /etc/lightdm/lightdm.conf with autologin options.


My /etc/lightdm/lightdm.conf is as follows:
```
[SeatDefaults]
allow-guest=false
autologin-guest=false
autologin-user=mytestuser
autologin-user-timeout=0
autologin-session=lightdm-autologin

```

There are only 2 users in my system: root, mytestuser.


When I "sudo kill xxxx" to kill X process, LightDM just shows a dialog to ask for username and password, while I expect an autologin.


/var/log/lightdm/lightdm.log says:
```
[+0.03s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.04s] DEBUG: Starting Light Display Manager 1.10.0, UID=0 PID=3505
[+0.04s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
[+0.04s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.04s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
[+0.04s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.04s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
[+0.04s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d
[+0.04s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d
[+0.04s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/10-xfce.conf
[+0.04s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.04s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.04s] DEBUG: Registered seat module xlocal
[+0.04s] DEBUG: Registered seat module xremote
[+0.04s] DEBUG: Registered seat module unity
[+0.04s] DEBUG: Registered seat module surfaceflinger
[+0.34s] DEBUG: Adding default seat
[+0.34s] DEBUG: Seat: Starting
[+0.34s] DEBUG: Seat: Creating user session
[+0.99s] DEBUG: Loading users from org.freedesktop.Accounts
[+1.08s] DEBUG: Seat: Creating display server of type x
[+1.08s] DEBUG: Deactivating Plymouth
[+1.11s] DEBUG: Using VT 7
[+1.11s] DEBUG: Seat: Starting local X display on VT 7
[+1.11s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+1.11s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+1.11s] DEBUG: DisplayServer x-0: Launching X Server
[+1.11s] DEBUG: Launching process 3713: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+1.11s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+1.11s] DEBUG: User /org/freedesktop/Accounts/User999 added
[+1.23s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+1.23s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+6.88s] DEBUG: Got signal 10 from process 3713
[+6.88s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+6.88s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+6.88s] DEBUG: Quitting Plymouth; retaining splash
[+6.91s] DEBUG: Seat: Display server ready, starting session authentication
[+6.91s] DEBUG: Session pid=4246: Started with service 'lightdm-autologin', username 'mytestuser'
[+6.93s] DEBUG: Session pid=4246: Authentication complete with return value 0: Success
[+6.93s] DEBUG: Seat: Session authenticated, running command
[+6.93s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+6.94s] DEBUG: Session pid=4246: Running command /usr/sbin/lightdm-session startxfce4
[+6.94s] DEBUG: Creating shared data directory /var/lib/lightdm-data/mytestuser
[+6.94s] DEBUG: Session pid=4246: Logging to .xsession-errors
[+6.94s] DEBUG: Activating VT 7
[+6.94s] DEBUG: Activating login1 session /org/freedesktop/login1/session/c6
[+191.16s] DEBUG: Session pid=4246: Exited with return value 0
[+191.16s] DEBUG: Seat: Session stopped
[+191.16s] DEBUG: Seat: Stopping display server, no sessions require it
[+191.16s] DEBUG: Sending signal 15 to process 3713
[+191.36s] DEBUG: Process 3713 exited with return value 0
[+191.36s] DEBUG: DisplayServer x-0: X server stopped
[+191.36s] DEBUG: Releasing VT 7
[+191.36s] DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0
[+191.36s] DEBUG: Seat: Display server stopped
[+191.36s] DEBUG: Seat: Active display server stopped, starting greeter
[+191.36s] DEBUG: Seat: Creating greeter session
[+191.37s] DEBUG: Seat: Creating display server of type x
[+191.37s] DEBUG: Using VT 7
[+191.37s] DEBUG: Seat: Starting local X display on VT 7
[+191.37s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+191.37s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+191.37s] DEBUG: DisplayServer x-0: Launching X Server
[+191.37s] DEBUG: Launching process 9629: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+191.37s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+191.43s] DEBUG: Got signal 10 from process 9629
[+191.43s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+191.43s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+191.43s] DEBUG: Seat: Display server ready, starting session authentication
[+191.43s] DEBUG: Session pid=9646: Started with service 'lightdm-greeter', username 'lightdm'
[+191.45s] DEBUG: Session pid=9646: Authentication complete with return value 0: Success
[+191.45s] DEBUG: Seat: Session authenticated, running command
[+191.45s] DEBUG: Session pid=9646: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/lightdm-gtk-greeter
[+191.45s] DEBUG: Creating shared data directory /var/lib/lightdm-data/lightdm
[+191.45s] DEBUG: Session pid=9646: Logging to /var/log/lightdm/x-0-greeter.log
[+191.53s] DEBUG: Activating VT 7
[+191.53s] DEBUG: Activating login1 session /org/freedesktop/login1/session/c8
[+191.69s] DEBUG: Session pid=9646: Greeter connected version=1.10.0
[+193.10s] DEBUG: Session pid=9646: Greeter start authentication
[+193.10s] DEBUG: Session pid=9701: Started with service 'lightdm', username '(null)'
[+193.11s] DEBUG: Session pid=9701: Got 1 message(s) from PAM
[+193.11s] DEBUG: Session pid=9646: Prompt greeter with 1 message(s)
[+195.42s] DEBUG: Session pid=9646: Greeter start authentication for mytestuser
[+195.42s] DEBUG: Session pid=9701: Sending SIGTERM
[+195.42s] DEBUG: Session pid=9716: Started with service 'lightdm', username 'mytestuser'
[+195.42s] DEBUG: Session pid=9701: Terminated with signal 15
[+195.42s] DEBUG: Session: Failed during authentication
[+195.42s] DEBUG: Seat: Session stopped
[+195.43s] DEBUG: Session pid=9716: Got 1 message(s) from PAM
[+195.43s] DEBUG: Session pid=9646: Prompt greeter with 1 message(s)
[+298.05s] DEBUG: Session pid=9646: Continue authentication
[+298.06s] DEBUG: Session pid=9716: Authentication complete with return value 0: Success
[+298.06s] DEBUG: Session pid=9646: Authenticate result for user mytestuser: Success
[+298.06s] DEBUG: Session pid=9646: User mytestuser authorized
[+298.06s] DEBUG: Session pid=9646: Greeter sets language zh_CN
[+298.07s] CRITICAL: g_dbus_connection_call_sync_internal: assertion 'object_path != NULL && g_variant_is_object_path (object_path)' failed
[+298.07s] DEBUG: Writing /home/mytestuser/.dmrc
[+298.12s] DEBUG: Session pid=9646: Greeter requests session xfce
[+298.12s] CRITICAL: g_dbus_connection_call_sync_internal: assertion 'object_path != NULL && g_variant_is_object_path (object_path)' failed
[+298.12s] DEBUG: Writing /home/mytestuser/.dmrc
[+298.27s] DEBUG: Seat: Stopping greeter; display server will be re-used for user session
[+298.27s] DEBUG: Session pid=9646: Sending SIGTERM
[+298.32s] DEBUG: Session pid=9646: Greeter closed communication channel
[+298.32s] DEBUG: Session pid=9646: Exited with return value 0
[+298.32s] DEBUG: Seat: Session stopped
[+298.32s] DEBUG: Seat: Greeter stopped, running session
[+298.32s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session1
[+298.33s] DEBUG: Session pid=9716: Running command /usr/sbin/lightdm-session startxfce4
[+298.33s] DEBUG: Creating shared data directory /var/lib/lightdm-data/mytestuser
[+298.33s] DEBUG: Session pid=9716: Logging to .xsession-errors
[+298.38s] DEBUG: Activating VT 7
[+298.38s] DEBUG: Activating login1 session /org/freedesktop/login1/session/c9

```

Let me explain this log.
1. [+0.03s]: On system boot, the first LightDM login: it's an autologin action as configured by lightdm.conf.
2. [+6.94s]: End of the first LightDM login, starts a session on VT 7.
3. [+191.16s]: I killed X process to emulate X crashing. LightDM detected this, and restarted a new greeter. Now a dialog showed and asked for username and password. I did not input username nor password now.
4. [+298.05s]: I input username and password, and hitted Login button.


So my question is: how to do autologin when X crashes?


Thx!

---

### Post by ajgreeny on 2014-11-24
I don't think you can.
It can be very useful if you have more than one available DE installed, eg kde and unity, but have set the system to autologin, as without the fallback of a login screen when you kill the xsession you would have to manually edit whatever config file is used to set the session chosen.

---

### Post by mcduck on 2014-11-24
I'd assume that behaviour is intentional, to avoid endless loop where something on your desktop would crash X, sending you through autologin back to desktop, crash again, etc..

Forcing you to login screen (without autologin) after X crash means you'll always have the option of switching to some other desktop session to fix whatever problem might have caused the crash.

---

### Post by hbb2 on 2015-04-08
> **McArthor_Lee said:**
> I find that LightDM cannot autologin my user when X crashes or when I kill X process, even if I configure /etc/lightdm/lightdm.conf with autologin options. ...

This issue is an official bug now:[URL="https://bugs.launchpad.net/lightdm/+bug/1396824"]
X server crash from autologin session returns to greeter, not autologin session [/URL]

---

### Post by deadflowr on 2015-05-04
I added a 5 second delay
```
autologin-user-timeout=5
```
Which seems to work fine, and does indeed reload the user's autologin session.
Haven't had the chance to crash a session ,but have routinely restarted lightdm.
My only problem with it is that 5 seconds is barely enough time to change different desktop sessions, if I want to.
(Since it seems like 4 of those seconds are the system reloading the display manager it self.)

I wonder if a 0(zero) timeout delay is too short for it to properly reload.

My 2 cents, on this probably would have died out thread...

---

