---
title: "lightdm fails(just blinking screen)"
date: 2011-10-28
forum: Desktop Environments
---

### Post by freaxtux on 2011-10-28
When I try to start lightdm shipped with xubuntu-desktop package, the screen just blinks.
I'm using lxdm instead at the moment, but it has some problem ([http://ubuntuforums.org/showthread.php?t=1871456](http://ubuntuforums.org/showthread.php?t=1871456))
I read log file, but couldn't find anything wrong.

I found a warning in the logfile and googled, but they say it appears to everybody.

This is the log file.
```

[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.0.1, UID=0 PID=1981
[+0.00s] DEBUG: Loaded configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registered seat module xlocal
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Adding default seat
[+0.00s] DEBUG: Starting seat

```
after this, next part appears repeatedly.
```

[+0.00s] DEBUG: Starting new display for greeter
[+0.00s] DEBUG: Starting local X display
[+0.00s] DEBUG: Using VT 7
[+0.01s] DEBUG: Activating VT 7
[+0.02s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+0.02s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+0.02s] DEBUG: Launching X Server
[+0.02s] DEBUG: Launching process 1986: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.03s] DEBUG: Waiting for ready signal from X server :0
[+0.04s] DEBUG: Acquired bus name
[+0.04s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+1.39s] DEBUG: Got signal 10 from process 1986
[+1.39s] DEBUG: Got signal from X server :0
[+1.39s] DEBUG: Connecting to XServer :0
[+1.40s] DEBUG: Starting greeter session
[+1.65s] DEBUG: pam_start("lightdm-autologin", "lightdm") -> (0x8c20088, 0)
[+1.65s] DEBUG: Starting session unity-greeter as user lightdm logging to /var/log/lightdm/x-0-greeter.log
[+1.66s] DEBUG: pam_authenticate(0x8c20088, 0) -> 0 (Success)
[+1.66s] DEBUG: pam_acct_mgmt(0x8c20088, 0) -> 0 (Success)
[+1.66s] DEBUG: Launching session
[+1.67s] DEBUG: pam_set_item(0x8c20088, 3, ":0") -> 0 (Success)
[+1.67s] DEBUG: pam_open_session(0x8c20088, 0) -> 0 (Success)
[+1.70s] DEBUG: Opened ConsoleKit session fafb29370bfd201066616b870000000c-1319041106.899262-1286802672
[+1.70s] DEBUG: Dropping privileges to uid 107
[+1.70s] DEBUG: Adding session authority to /var/lib/lightdm/.Xauthority
[+1.78s] DEBUG: Restoring privileges
[+1.78s] DEBUG: Launching process 2003: /usr/lib/lightdm/lightdm-greeter-session 'unity-greeter'
[+1.78s] WARNING: Failed to open log file /var/log/lightdm/x-0-greeter.log: Permission denied
[+1.78s] DEBUG: pam_setcred(0x8c20088, PAM_ESTABLISH_CRED) -> 0 (Success)
[+1.78s] DEBUG: PAM returns environment 'PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games LANG=ko_KR.UTF-8'
[+1.96s] DEBUG: Read 8 bytes from greeter
[+1.96s] DEBUG: Read 9 bytes from greeter
[+1.96s] DEBUG: Greeter connected version=1.0.1
[+1.96s] DEBUG: Wrote 99 bytes to greeter
[+1.96s] DEBUG: Greeter connected, display is ready
[+1.96s] DEBUG: New display ready, switching to it
[+1.96s] DEBUG: Activating VT 7
[+1.96s] DEBUG: Process 2003 exited with return value 0
[+1.96s] DEBUG: pam_close_session(0x8c20088) -> 0 (Success)
[+1.96s] DEBUG: pam_setcred(0x8c20088, PAM_DELETE_CRED) -> 0 (Success)
[+1.96s] DEBUG: pam_end(0x8c20088) -> 0
[+1.96s] DEBUG: Ending ConsoleKit session fafb29370bfd201066616b870000000c-1319041106.899262-1286802672
[+1.99s] DEBUG: Greeter quit
[+1.99s] DEBUG: Stopping display
[+1.99s] DEBUG: Sending signal 15 to process 1986
[+1.99s] DEBUG: Dropping privileges to uid 107
[+1.99s] DEBUG: Removing session authority from /var/lib/lightdm/.Xauthority
[+2.06s] DEBUG: Restoring privileges
[+2.07s] DEBUG: Process 1986 exited with return value 0
[+2.07s] DEBUG: X server stopped
[+2.07s] DEBUG: Removing X server authority /var/run/lightdm/root/:0
[+2.07s] DEBUG: Releasing VT 7
[+2.07s] DEBUG: Display server stopped
[+2.07s] DEBUG: Display stopped
[+2.07s] DEBUG: Active display stopped, switching to greeter
[+2.07s] DEBUG: Switching to greeter

```

thanks.

---

### Post by freaxtux on 2011-10-30
The Lubuntu is 11.10 version and was installed with USB. 
"Check disc for defects" menu didn't report any error.
Xubuntu-desktop is installed now.

---

### Post by bimaljr on 2011-11-04
Same issue, please help

---

### Post by freaxtux on 2011-11-09
> **bimaljr said:**
> Same issue, please help

If you want to use another DM temporarily, you can use Recovery mode when you boot. 

Select remount menu, and then drop to root shell.

type "dpkg-reconfigure lightdm", and then select whatever DM you want to use.

Anyway, I still can't find how to fix this problem. Anybody knows how?

---

### Post by Elfy on 2011-11-09
Does lubuntu use the unity-greeter? If it doesn't or shouldn't it could be  that - I've been playing with lightdm in xubuntu - if you want to use unity-greeter in that then you also need gnome-settings-daemon - if that's not there in lubuntu it could be the issue.

> /usr/lib/lightdm/lightdm-greeter-session 'unity-greeter'

I'm assuming you don't get the same problem in Xubuntu.

---

### Post by gmargo on 2011-11-12
> **freaxtux said:**
> When I try to start lightdm shipped with xubuntu-desktop package, the screen just blinks.


I had the same problem, and it was due to **unity-greeter** segfaulting (visible in /var/log/kern.log).

I purged **unity-greeter** and installed **lightdm-gtk-greeter**, and modified /etc/lightdm/lightdm.conf to use "greeter-session=lightdm-gtk-greeter".

---

### Post by freaxtux on 2011-11-15
> **forestpiskie said:**
> Does lubuntu use the unity-greeter? If it doesn't or shouldn't it could be  that - I've been playing with lightdm in xubuntu - if you want to use unity-greeter in that then you also need gnome-settings-daemon - if that's not there in lubuntu it could be the issue.



I'm assuming you don't get the same problem in Xubuntu.

I installed gnome-settings-daemon. Now it works. Thank you.

---

### Post by Elfy on 2011-11-15
Welcome - can you mark thread solved please.

---

