---
title: "Desktop does not load after upgrade to 13.04"
date: 2013-11-10
forum: Desktop Environments
---

### Post by harmti on 2013-11-10
I upgraded my Ubuntu server from 12.04 to 13.04 a few months back. Something went wrong in the upgrade, and I haven't been able to use the desktop since. Login works, but desktop never loads properly, there's just an empty screen with a mouse pointer. I have tried re-installing ubuntu-desktop, resetting comzip settings, installing lubuntu-desktop and further upgrading to 13.10, but nothing has helped. It may well be that I have just managed to further mess the things up. Any ideas what to try, or should I just re-install from scratch?
 
/var/log/lightdm.log
```
[+0.03s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+0.03s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+0.03s] DEBUG: DisplayServer x-0: Launching X Server
[+0.03s] DEBUG: Launching process 2085: /usr/bin/X -core :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.03s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+0.03s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.03s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.08s] DEBUG: Got signal 10 from process 2085
[+0.08s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+0.08s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+0.08s] DEBUG: Quitting Plymouth; retaining splash
[+0.10s] DEBUG: Seat: Display server ready, starting session authentication
[+0.10s] DEBUG: Session: Setting XDG_VTNR=7
[+0.10s] DEBUG: Session pid=2241: Started with service 'lightdm-greeter', username 'lightdm'
[+0.14s] DEBUG: Session pid=2241: Authentication complete with return value 0: Success
[+0.14s] DEBUG: Seat: Session authenticated, running command
[+0.14s] DEBUG: Session pid=2241: Setting XDG_VTNR=7
[+0.14s] DEBUG: Session pid=2241: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+0.15s] DEBUG: Session pid=2241: Logging to /var/log/lightdm/x-0-greeter.log
[+0.16s] DEBUG: Activating VT 7
[+0.25s] DEBUG: Session pid=2241: Greeter connected version=1.8.4
[+0.37s] DEBUG: Session pid=2241: Greeter start authentication for timo
[+0.37s] DEBUG: Seat: Setting XDG_SEAT=seat0
[+0.37s] DEBUG: Session: Setting XDG_VTNR=7
[+0.37s] DEBUG: Session pid=2560: Started with service 'lightdm', username 'timo'
[+0.37s] DEBUG: Session pid=2241: Greeter start authentication for timo
[+0.37s] DEBUG: Session pid=2560: Sending SIGTERM
[+0.37s] DEBUG: Seat: Setting XDG_SEAT=seat0
[+0.37s] DEBUG: Session: Setting XDG_VTNR=7
[+0.37s] DEBUG: Session pid=2562: Started with service 'lightdm', username 'timo'
[+0.37s] DEBUG: Session pid=2560: Terminated with signal 15
[+0.37s] DEBUG: Session: Failed during authentication
[+0.37s] DEBUG: Seat: Session stopped
[+0.37s] DEBUG: Session pid=2562: Got 1 message(s) from PAM
[+0.37s] DEBUG: Session pid=2241: Prompt greeter with 1 message(s)
[+5.20s] DEBUG: Session pid=2241: Continue authentication
[+5.22s] DEBUG: Session pid=2562: Authentication complete with return value 0: Success
[+5.22s] DEBUG: Session pid=2241: Authenticate result for user timo: Success
[+5.22s] DEBUG: Session pid=2241: User timo authorized
[+5.23s] DEBUG: Session pid=2241: Greeter requests session ubuntu
[+5.23s] DEBUG: Writing /home/timo/.dmrc
[+5.24s] DEBUG: Seat: Stopping greeter; display server will be re-used for user session
[+5.24s] DEBUG: Session pid=2241: Sending SIGTERM
[+5.25s] DEBUG: Session pid=2241: Exited with return value 0
[+5.25s] DEBUG: Seat: Session stopped
[+5.25s] DEBUG: Seat: Greeter stopped, running session
[+5.25s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+5.25s] DEBUG: Session pid=2562: Setting XDG_VTNR=7
[+5.25s] DEBUG: Session pid=2562: Running command /usr/sbin/lightdm-session gnome-session --session=ubuntu
[+5.25s] DEBUG: Session pid=2562: Logging to .xsession-errors
[+5.26s] DEBUG: Activating VT 7

```

.xsession-errors:
```
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  22
  Current serial number in output stream:  22
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd respawning too fast, stopped
```

---

### Post by Igmu on 2013-11-27
I am having the same issue. I tried dist upgrade from 12.04 to 13.10. Login screen still displays 12.04 lts. After succesful login, just displays desktop wallpaper, mouse pointer... no panels. Tried sudo lightdm in tty1(with password) only to result "Failed to use bus name org.freedesktop.DisplayManager, do you have the appropriate permissions?"

---

### Post by harmti on 2013-12-01
[FONT=arial]I finally managed to resolve my issue. I hadn't noticed earlier "(EE) GLX error: Can not get required symbols" in Xorg.0.log. This led to case [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1076787](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1076787). [/FONT]

[FONT=arial]I have Radeon HD 6450, but don't remember installing fglrx, still there were some fglrx components on the system. Uninstalling fglrx-amdcccle-updates and fglrx-updates already helped, desktop started to load but still without the Ubuntu menu. After removing my .config folder things finally resolved. [/FONT][FONT=arial]
[/FONT]
[FONT=arial]Hope this helps others too.[/FONT]
[FONT=arial]
[/FONT]

---

