---
title: "gdm disconnects when using domain login"
date: 2014-06-20
forum: Desktop Environments
---

### Post by edubidu on 2014-06-20
Hi forum,

Not sure if I post at the right place.
The following problem seems to be in relation with gnome:

- Installed ubuntu 14.04 LTS amd desktop
- I'd like to connect the machine to Active Directory. 
- Installed this: 
```
http://www.sinap.si/wp-content/uploads/2011/08/LikewiseOpen-6.0.0.8388-linux-amd64-deb.sh
```

- Added the computer successfully. **Login works in terminal**, but gdm disconnects immediately.

cat /var/log/auth.log
```

...
Jun 17 12:13:18 mycomp polkitd(authority=local): Registered  Authentication Agent for unix-session:c1 (system bus name :1.36  [gnome-shell --mode=gdm], object path  /org/freedesktop/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Jun 17 12:13:35 mycomp gdm-password][2199]:  pam_succeed_if(gdm-password:auth): requirement "user ingroup  nopasswdlogin" not met by user "DOMAIN\adusername"
Jun 17 12:13:45 mycomp gdm-password][2199]:  pam_unix(gdm-password:session): session opened for user adusername by  (unknown)(uid=0)
Jun 17 12:13:45 mycomp gdm-launch-environment][1685]: pam_unix(gdm-launch-environment:session): session closed for user gdm
Jun 17 12:13:45 mycomp polkitd(authority=local): Unregistered  Authentication Agent for unix-session:c1 (system bus name :1.36, object  path /org/freedesktop/PolicyKit1/AuthenticationAgent, locale  en_US.UTF-8) (disconnected from bus)
Jun 17 12:13:46 mycomp gdm-password][2199]: pam_unix(gdm-password:session): session closed for user adusername
Jun 17 12:13:46 mycomp dbus[735]: [system] Rejected send message, 1  matched rules; type="method_call", sender=":1.11" (uid=0 pid=996  comm="gdm ") interface="org.freedesktop.DBus.Properties" member="GetAll"  error name="(unset)" requested_reply="0" destination=":1.43" (uid=0  pid=2357 comm="/usr/lib/gdm/gdm-simple-slave --display-id /org/gn")
...

```

Some ideas? I googled around but cannot find anything for ubuntu...

---

### Post by edubidu on 2014-06-25
Some more information: startx works, but then I get the following msgs in .xsession-errors:

```
adusername@mycomp:/home/local/DOMAIN/adusername# cat .xsession-errors
Xsession: X session started for adusername at Mit Jun 25 10:41:04 CEST 2014
localuser:adusername being added to access control list
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
libGL error: failed to open drm device: Permission denied
libGL error: failed to load driver: r600
gnome-session-is-accelerated: llvmpipe detected.
x-session-manager[20187]: WARNING: Could not get session id for session. Check that logind is properly installed and pam_systemd is getting used at login.
x-session-manager[20187]: WARNING: Could not parse desktop file update-notifier.desktop or it references a not found TryExec binary
GNOME_KEYRING_CONTROL=/home/local/DOMAIN/adusername/.cache/keyring-JZZWC0
GPG_AGENT_INFO=/home/local/DOMAIN/adusername/.cache/keyring-JZZWC0/gpg:0:1
GNOME_KEYRING_PID=20272
GNOME_KEYRING_CONTROL=/home/local/DOMAIN/adusername/.cache/keyring-JZZWC0
GPG_AGENT_INFO=/home/local/DOMAIN/adusername/.cache/keyring-JZZWC0/gpg:0:1
GNOME_KEYRING_CONTROL=/home/local/DOMAIN/adusername/.cache/keyring-JZZWC0
GPG_AGENT_INFO=/home/local/DOMAIN/adusername/.cache/keyring-JZZWC0/gpg:0:1
GNOME_KEYRING_CONTROL=/home/local/DOMAIN/adusername/.cache/keyring-JZZWC0
GPG_AGENT_INFO=/home/local/DOMAIN/adusername/.cache/keyring-JZZWC0/gpg:0:1
SSH_AUTH_SOCK=/home/local/DOMAIN/adusername/.cache/keyring-JZZWC0/ssh

** (gnome-settings-daemon:20285): WARNING **: Name taken or bus went away - shutting down

(unity-settings-daemon:20280): power-plugin-WARNING **: Unable to inhibit lid switch: GDBus.Error:org.freedesktop.DBus.Error.AccessDenied: Operation not permitted
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp

(unity-settings-daemon:20280): media-keys-plugin-WARNING **: Unable to inhibit keypresses: GDBus.Error:org.freedesktop.DBus.Error.AccessDenied: Operation not permitted

** (process:20329): WARNING **: killswitch.vala:103: Can't open /dev/rfkill for use as a killswitch backend: Permission denied

** (process:20329): CRITICAL **: bluez.vala:104: GDBus.Error:org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 2 matched rules; type="method_call", sender=":1.578" (uid=64500822 pid=20329 comm="/usr/lib/x86_64-linux-gnu/indicator-bluetooth/indi") interface="org.bluez.Manager" member="DefaultAdapter" error name="(unset)" requested_reply="0" destination="org.bluez" (uid=0 pid=745 comm="/usr/sbin/bluetoothd ")
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
initctl: UPSTART_SESSION isn't set in the environment. Unable to locate the Upstart instance.
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Starting plugin: opengl

(unity-settings-daemon:20280): color-plugin-WARNING **: failed to create device: failed to obtain org.freedesktop.color-manager.create-device auth
libGL error: failed to open drm device: Permission denied
libGL error: failed to load driver: r600

** (process:20331): CRITICAL **: volume_control_set_volume_internal: assertion '_tmp1_ == PA_CONTEXT_READY' failed

** (process:20331): CRITICAL **: file /build/buildd/indicator-sound-12.10.2+14.04.20140401/obj-x86_64-linux-gnu/src/volume-control.c: line 1775: uncaught error: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: No such interface (g-dbus-error-quark, 16)

(polkit-gnome-authentication-agent-1:20347): polkit-gnome-1-WARNING **: Unable to determine the session we are in: No session for pid 20347

(unity-settings-daemon:20280): color-plugin-WARNING **: failed to obtain org.freedesktop.color-manager.create-profile auth
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
I/O warning : failed to load external entity "/home/local/DOMAIN/adusername/.compiz/session/10c5330511b9c4d781140368566472849000000201870001"
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom

(nm-applet:20327): nm-applet-WARNING **: Failed to register as an agent: (32) Session not found

(nm-applet:20327): nm-applet-WARNING **: Failed to register as an agent: (32) Session not found

(unity-settings-daemon:20280): AccountsService-WARNING **: SetInputSources call failed: GDBus.Error:org.freedesktop.Accounts.Error.PermissionDenied: Not authorized
compiz (core) - Warn: Attempted to restack relative to 0x12000cd which is not a child of the root window or a window compiz owns
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
gtk-window-decorator: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.0.
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":1"
      after 4096 requests (4096 known processed) with 0 events remaining.
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : Default
```

---

### Post by edubidu on 2014-06-25
/var/log/syslog
```
Jun 25 10:38:52 mycomp kernel: [ 3360.313804] type=1400 audit(1403685532.128:127): apparmor="DENIED" operation="open" profile="/usr/lib/telepathy/mission-control-5" name="/home/local/DOMAIN/adusername/.cache/dconf/user" pid=20035 comm="mission-control" requested_mask="rwc" denied_mask="rwc" fsuid=64500822 ouid=64500822
```

Seems to be the same problem like this treat, but the suggested solutions don't work for me:
[http://askubuntu.com/questions/231784/log-in-fails-and-returns-to-log-in-screen](http://askubuntu.com/questions/231784/log-in-fails-and-returns-to-log-in-screen)

---

### Post by edubidu on 2014-06-25
Seems to be the same problem like this, but the proposed solutions don't work:
[http://askubuntu.com/questions/231784/log-in-fails-and-returns-to-log-in-screen](http://askubuntu.com/questions/231784/log-in-fails-and-returns-to-log-in-screen)

---

### Post by psyduckbug on 2014-06-30
I have the same problema, thanks edibidu

---

### Post by edubidu on 2014-06-30
> **psyduckbug said:**
> I have the same problema, thanks edibidu

Hi,
unfortunately the forum seems to be dead. I get no help. I just found this:
[http://ubuntuforums.org/showthread.php?t=2219245&](http://ubuntuforums.org/showthread.php?t=2219245&)
:(

---

### Post by edubidu on 2014-07-01
SOLVED

```
vi /etc/pam.d/common-session 
```


change the line that reads:  ```
session sufficient pam_lsass.so
```
  to
  ```
session [success=ok default=ignore] pam_lsass.so
```

---

