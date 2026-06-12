---
title: "no login screen after switching to lightdm-webkit-greeter"
date: 2013-08-11
forum: Desktop Environments
---

### Post by system76panp9 on 2013-08-11
in Ubuntu 13.04 I really would like to use webkit greeter so I installed package lightdm-webkit-greeter
and got no errors, then I changed greeter-session in lightdm.conf to = lightdm-webkit-greeter
and then when I start up instead of login screen I get just black screen and I have to type
Ctrl-Alt-F1 to get a login prompt so I changed lightdm.conf back to say greeter-session=unity-greeter
which is back to square 1, I wonder if I am missing something or at least where I could try to debug
this to figure out what is going wrong, I really did nothing except install the package and edit the
one line of the lightdm configuration, and as a result nearly got locked out of my system, so I would
really appreciate some help, thanks

---

### Post by stinkeye on 2013-08-12
I think it may be buggy.
I installed both lightdm-webkit-greeter and lightdm-gtk-greeter.

After editing **/etc/lightdm/lightdm.conf** to load the appropriate greeter, both unity-greeter and lightdm-gtk-greeter loaded  fine,
but lightdm-webkit-greeter would mostly fail to a black screen.
Occasionally it would load, to show as in the last attached pic.

I tested in terminal using the command....
```
lightdm -d --test-mode
```

When it works using lightdm-webkit-greeter ...(note the last 4 lines)
```
glen@Raring:~$ lightdm -d --test-mode
[+0.00s] DEBUG: Logging to /home/glen/.cache/lightdm/log/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.6.0, UID=1000 PID=14845
[+0.00s] DEBUG: Loaded configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Running in user mode
[+0.00s] DEBUG: Using Xephyr for X servers
[+0.00s] DEBUG: Registered seat module xlocal
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Adding default seat
[+0.00s] DEBUG: Starting seat
[+0.00s] DEBUG: Starting new display for greeter
[+0.00s] DEBUG: Starting local X display
[+0.01s] DEBUG: Logging to /home/glen/.cache/lightdm/log/x-1.log
[+0.01s] DEBUG: Writing X server authority to /home/glen/.cache/lightdm/run/root/:1
[+0.01s] DEBUG: Launching X Server
[+0.01s] DEBUG: Launching process 14850: /usr/bin/Xephyr :1 -core -auth /home/glen/.cache/lightdm/run/root/:1 -nolisten tcp
[+0.01s] DEBUG: Waiting for ready signal from X server :1
[+0.01s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.02s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.06s] DEBUG: Got signal 10 from process 14850
[+0.06s] DEBUG: Got signal from X server :1
[+0.06s] DEBUG: Connecting to XServer :1
[+0.06s] DEBUG: Starting greeter
[+0.07s] DEBUG: Started session 14853 with service 'lightdm-greeter', username 'glen'
[+0.09s] DEBUG: Session 14853 authentication complete with return value 0: Success
[+0.09s] DEBUG: Greeter authorized
[+0.10s] DEBUG: Launching process 14855: /usr/bin/numlockx on
[+0.11s] DEBUG: Process 14855 exited with return value 0
[+0.11s] DEBUG: Exit status of /usr/bin/numlockx on: 0
[+0.11s] DEBUG: Logging to /home/glen/.cache/lightdm/log/x-1-greeter.log
[COLOR="#FF0000"][+0.11s] DEBUG: Session 14853 running command /usr/lib/lightdm/lightdm-greeter-session /usr/bin/lightdm-webkit-greeter[/COLOR]
[+0.20s] DEBUG: Greeter connected version=1.6.0
[+0.20s] DEBUG: Greeter connected, display is ready
[+0.20s] DEBUG: New display ready, switching to it
```


When it fails the last 3 lines are missing  but no error
```
glen@Raring:~$ lightdm -d --test-mode
[+0.00s] DEBUG: Logging to /home/glen/.cache/lightdm/log/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.6.0, UID=1000 PID=15575
[+0.00s] DEBUG: Loaded configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Running in user mode
[+0.00s] DEBUG: Using Xephyr for X servers
[+0.00s] DEBUG: Registered seat module xlocal
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Adding default seat
[+0.00s] DEBUG: Starting seat
[+0.00s] DEBUG: Starting new display for greeter
[+0.00s] DEBUG: Starting local X display
[+0.01s] DEBUG: Logging to /home/glen/.cache/lightdm/log/x-1.log
[+0.01s] DEBUG: Writing X server authority to /home/glen/.cache/lightdm/run/root/:1
[+0.01s] DEBUG: Launching X Server
[+0.02s] DEBUG: Launching process 15580: /usr/bin/Xephyr :1 -core -auth /home/glen/.cache/lightdm/run/root/:1 -nolisten tcp
[+0.02s] DEBUG: Waiting for ready signal from X server :1
[+0.02s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.02s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.07s] DEBUG: Got signal 10 from process 15580
[+0.07s] DEBUG: Got signal from X server :1
[+0.07s] DEBUG: Connecting to XServer :1
[+0.08s] DEBUG: Starting greeter
[+0.09s] DEBUG: Started session 15583 with service 'lightdm-greeter', username 'glen'
[+0.11s] DEBUG: Session 15583 authentication complete with return value 0: Success
[+0.11s] DEBUG: Greeter authorized
[+0.12s] DEBUG: Launching process 15585: /usr/bin/numlockx on
[+0.13s] DEBUG: Process 15585 exited with return value 0
[+0.13s] DEBUG: Exit status of /usr/bin/numlockx on: 0
[+0.13s] DEBUG: Logging to /home/glen/.cache/lightdm/log/x-1-greeter.log
[COLOR="#FF0000"][+0.13s] DEBUG: Session 15583 running command /usr/lib/lightdm/lightdm-greeter-session /usr/bin/lightdm-webkit-greeter[/COLOR]
```

---

