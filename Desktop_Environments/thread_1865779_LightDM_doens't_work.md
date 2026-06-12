---
title: "LightDM doens't work"
date: 2011-10-20
forum: Desktop Environments
---

### Post by gnagnibu on 2011-10-20
Hi everybody.
Today I installed LightDM but it doesn't work.

/var/log/lightdm/lightdm.log says

```

[+67.15s] DEBUG: Sending signal 15 to process 23593
[+67.15s] DEBUG: Dropping privileges to uid 115
[+67.15s] DEBUG: Removing session authority from /var/lib/lightdm/.Xauthority
[+67.18s] DEBUG: Restoring privileges
[+67.53s] DEBUG: Process 23593 exited with return value 0
[+67.53s] DEBUG: X server stopped
[+67.53s] DEBUG: Removing X server authority /var/run/lightdm/root/:0
[+67.53s] DEBUG: Releasing VT 7
[+67.53s] DEBUG: Display server stopped
[+67.53s] DEBUG: Display stopped
[+67.53s] DEBUG: Active display stopped, switching to greeter
[+67.53s] DEBUG: Switching to greeter
[+67.53s] DEBUG: Starting new display for greeter
[+67.53s] DEBUG: Starting local X display
[+67.53s] DEBUG: Using VT 7
[+67.53s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+67.53s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+67.53s] DEBUG: Launching X Server
[+67.53s] DEBUG: Launching process 23622: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+67.53s] DEBUG: Waiting for ready signal from X server :0
[+68.22s] DEBUG: Got signal 10 from process 23622
[+68.22s] DEBUG: Got signal from X server :0
[+68.22s] DEBUG: Connecting to XServer :0
[+68.22s] DEBUG: Error connecting to XServer :0
[+74.25s] DEBUG: Got signal 15 from process 1
[+74.25s] DEBUG: Caught Terminated signal, shutting down
[+74.25s] DEBUG: Stopping display manager
[+74.25s] DEBUG: Stopping seat
[+74.25s] DEBUG: Stopping display
[+74.25s] DEBUG: Sending signal 15 to process 23622
[+74.28s] DEBUG: Process 23622 exited with return value 0
[+74.28s] DEBUG: X server stopped
[+74.28s] DEBUG: Removing X server authority /var/run/lightdm/root/:0
[+74.28s] DEBUG: Releasing VT 7
[+74.28s] DEBUG: Display server stopped
[+74.28s] DEBUG: Display stopped
[+74.28s] DEBUG: Seat stopped
[+74.28s] DEBUG: Display manager stopped
[+74.28s] DEBUG: Stopping Light Display Manager

```

and /var/log/lightdm/x-0.log says

```

X.Org X Server 1.10.4
Release Date: 2011-08-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux gnagniPC 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=/dev/sdb1 ro
Build Date: 13 October 2011  05:44:30PM
xorg-server 2:1.10.4-1ubuntu4.1 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.22.2
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Oct 20 19:32:53 2011
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) Failed to load module "nv" (module does not exist, 0)
(EE) open /dev/fb0: No such file or directory
 ddxSigGiveUp: Closing log

```

I use nvidia drivers and KDM works, I can't understand why xorg try to use nv driver when launching lightdm.

Any ideas?

---

### Post by drem on 2011-11-09
Hello, 
I had the same problem. Try:
```

sudo apt-get install gnome-setting-daemon

```

You can also modify the background:
```

sudo kate /etc/lightdm/unity-greeter.conf

```

and replace

```
background=/usr/share/backgrounds/warty-final-ubuntu.png

```
with
```

background=/usr/share/wallpapers/kde-default.png

```

---

### Post by gnagnibu on 2011-11-09
Thanks man!
It works now ;)

---

