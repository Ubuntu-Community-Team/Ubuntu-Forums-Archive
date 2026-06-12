---
title: "Problem with lightdm in Ubuntu 12.04"
date: 2013-06-28
forum: Desktop Environments
---

### Post by rmccarri on 2013-06-28
Hi Everyone,
I restarted my computer earlier today and when it came back up, it got stuck on the purple Ubuntu splash screen.  The system still booted, so I was able to SSH in and after doing some internet searching it seemed that lightdm was the issue.  I uninstalled and purged it and everything starts up with the gdm.  I've tried installing lightdm a few times to no avail.  Here is the lightdm log file:

```
[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.2.3, UID=0 PID=1241
[+0.00s] DEBUG: Loaded configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registered seat module xlocal
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Adding default seat
[+0.00s] DEBUG: Starting seat
[+0.00s] DEBUG: Starting new display for greeter
[+0.00s] DEBUG: Starting local X display
[+0.08s] DEBUG: X server :0 will replace Plymouth
[+0.10s] DEBUG: Using VT 7
[+0.10s] DEBUG: Activating VT 7
[+0.10s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+0.11s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+0.11s] DEBUG: Launching X Server
[+0.11s] DEBUG: Launching process 1306: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none
[+0.11s] DEBUG: Waiting for ready signal from X server :0
[+0.11s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.11s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.11s] DEBUG: Process 1306 exited with return value 1
[+0.11s] DEBUG: X server stopped
[+0.11s] DEBUG: Removing X server authority /var/run/lightdm/root/:0
[+0.11s] DEBUG: Releasing VT 7
[+0.11s] DEBUG: Stopping Plymouth, X server failed to start
[+0.12s] DEBUG: Display server stopped
[+0.12s] DEBUG: Stopping display
[+0.12s] DEBUG: Display stopped
[+0.12s] DEBUG: Stopping X local seat, failed to start a display
[+0.12s] DEBUG: Stopping seat
[+0.12s] DEBUG: Seat stopped
[+0.12s] DEBUG: Required seat has stopped
[+0.12s] DEBUG: Stopping display manager
[+0.12s] DEBUG: Display manager stopped
[+0.12s] DEBUG: Stopping daemon
[+0.12s] DEBUG: Exiting with return value 1
```

I can run with gdm and it seems that it's more stable in general.  However, there is a slightly longer lag when booting (I've got a pretty fast computer running off an SSD that boots almost instantly with lightdm).  I also prefer the unity-greeter visually.  Has anyone else run into this issue and found a fix?  I've also reinstalled the nvidia drivers and tried a different version as it seems that can cause issues.  I've also gone with a default background as I've also seen that background outside of the default locations have caused issues as well.  Any insight would be greatly appreciated!
Thanks,
Rob

---

### Post by grahammechanical on 2013-06-28
We can install more than one display manager but we can only use one at a time. There was no need to uninstall lightdm. Just install gdm and then stop lightdm and start gdm. If you have installed lighdm you can switch back over by running these commands.

```
sudo service gdm stop
```
```
sudo service lightdm start
```

You might also find this information useful

[http://www.webupd8.org/2013/01/ubuntu-lightdm-black-screen-when-using.html](http://www.webupd8.org/2013/01/ubuntu-lightdm-black-screen-when-using.html)

[http://www.webupd8.org/2011/07/how-to-switch-between-gdm-lightdm-or.html](http://www.webupd8.org/2011/07/how-to-switch-between-gdm-lightdm-or.html)

Regards.

---

