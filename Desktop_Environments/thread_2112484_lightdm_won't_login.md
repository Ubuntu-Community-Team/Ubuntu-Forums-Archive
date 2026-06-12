---
title: "lightdm won't login ??"
date: 2013-02-04
forum: Desktop Environments
---

### Post by einstein**-7 on 2013-02-04
Hey all I'm having problems getting lighdm to work.  Gdm works fine and logs in but lightdm wont log in my main user -- other users work. I've tried multiple greeters,
lightdm-gtk-greeter
lightdm-kde-greeter
unity-greeter
all have the same problem.
thanks all,

---

### Post by einstein**-7 on 2013-02-04
Here are the logs

lightdm.log
[```
+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.2.1, UID=0 PID=5258
[+0.00s] DEBUG: Loaded configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registered seat module xlocal
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Adding default seat
[+0.00s] DEBUG: Starting seat
[+0.00s] DEBUG: Starting new display for greeter
[+0.00s] DEBUG: Starting local X display
[+0.00s] DEBUG: Using VT 7
[+0.00s] DEBUG: Activating VT 7
[+0.01s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+0.01s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+0.01s] DEBUG: Launching X Server
[+0.01s] DEBUG: Launching process 5264: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.01s] DEBUG: Waiting for ready signal from X server :0
[+0.01s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.01s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+1.46s] DEBUG: Got signal 10 from process 5264
[+1.46s] DEBUG: Got signal from X server :0
[+1.46s] DEBUG: Connecting to XServer :0
[+1.47s] DEBUG: Starting greeter
[+1.47s] DEBUG: Started session 5268 with service 'lightdm', username 'lightdm'
[+1.53s] DEBUG: Session 5268 authentication complete with return value 0: Success
[+1.53s] DEBUG: Greeter authorized
[+1.53s] DEBUG: Logging to /var/log/lightdm/x-0-greeter.log
[+1.56s] DEBUG: Session 5268 running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+1.97s] DEBUG: Greeter connected version=1.2.1
[+1.97s] DEBUG: Greeter connected, display is ready
[+1.97s] DEBUG: New display ready, switching to it
[+1.97s] DEBUG: Activating VT 7
[+2.67s] DEBUG: Greeter start authentication for crush
[+2.67s] DEBUG: Started session 5335 with service 'lightdm', username 'crush'
[+2.69s] DEBUG: Session 5335 got 1 message(s) from PAM
[+2.69s] DEBUG: Prompt greeter with 1 message(s)
[+12.62s] DEBUG: Continue authentication
[+12.79s] DEBUG: Session 5335 authentication complete with return value 0: Success
[+12.79s] DEBUG: Authenticate result for user crush: Success
[+12.79s] DEBUG: User crush authorized
[+12.79s] DEBUG: Greeter requests session ubuntu
[+12.79s] DEBUG: Using session ubuntu
[+12.79s] DEBUG: Stopping greeter
[+12.79s] DEBUG: Session 5268: Sending SIGTERM
[+12.82s] DEBUG: Session 5268 exited with return value 0
[+12.82s] DEBUG: Greeter quit
[+12.83s] DEBUG: Dropping privileges to uid 1000
[+12.83s] DEBUG: Restoring privileges
[+12.84s] DEBUG: Dropping privileges to uid 1000
[+12.84s] DEBUG: Writing /home/crush/.dmrc
[+12.90s] DEBUG: Restoring privileges
[+12.95s] DEBUG: Starting session ubuntu as user crush
[+12.95s] DEBUG: Session 5335 running command /usr/sbin/lightdm-session gnome-session --session=ubuntu
[+12.98s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+12.98s] DEBUG: Session 5335 exited with return value 1
[+12.98s] DEBUG: User session quit
[+12.98s] DEBUG: Stopping display
[+12.98s] DEBUG: Sending signal 15 to process 5264
[+13.14s] DEBUG: Greeter closed communication channel
[+13.68s] DEBUG: Process 5264 exited with return value 0
[+13.68s] DEBUG: X server stopped
[+13.68s] DEBUG: Removing X server authority /var/run/lightdm/root/:0
[+13.68s] DEBUG: Releasing VT 7
[+13.68s] DEBUG: Display server stopped
[+13.68s] DEBUG: Display stopped
[+13.68s] DEBUG: Active display stopped, switching to greeter
[+13.68s] DEBUG: Switching to greeter
[+13.68s] DEBUG: Starting new display for greeter
[+13.68s] DEBUG: Starting local X display
[+13.68s] DEBUG: Using VT 7
[+13.68s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+13.68s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+13.68s] DEBUG: Launching X Server
[+13.68s] DEBUG: Launching process 5410: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+13.68s] DEBUG: Waiting for ready signal from X server :0
[+15.09s] DEBUG: Got signal 10 from process 5410
[+15.09s] DEBUG: Got signal from X server :0
[+15.09s] DEBUG: Connecting to XServer :0
[+15.09s] DEBUG: Starting greeter
[+15.09s] DEBUG: Started session 5413 with service 'lightdm', username 'lightdm'
[+15.13s] DEBUG: Session 5413 authentication complete with return value 0: Success
[+15.13s] DEBUG: Greeter authorized
[+15.13s] DEBUG: Logging to /var/log/lightdm/x-0-greeter.log
[+15.13s] DEBUG: Session 5413 running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+15.35s] DEBUG: Greeter connected version=1.2.1
[+15.35s] DEBUG: Greeter connected, display is ready
[+15.35s] DEBUG: New display ready, switching to it
[+15.35s] DEBUG: Activating VT 7
[+15.35s] DEBUG: Stopping greeter display being switched from
[+15.61s] DEBUG: Greeter start authentication for crush
[+15.61s] DEBUG: Started session 5480 with service 'lightdm', username 'crush'
[+15.63s] DEBUG: Session 5480 got 1 message(s) from PAM
[+15.63s] DEBUG: Prompt greeter with 1 message(s)
[+29.12s] DEBUG: Got signal 15 from process 1
[+29.12s] DEBUG: Caught Terminated signal, shutting down
[+29.12s] DEBUG: Stopping display manager
[+29.12s] DEBUG: Stopping seat
[+29.12s] DEBUG: Stopping display
[+29.12s] DEBUG: Session 5413: Sending SIGTERM
[+29.13s] DEBUG: Session 5480 terminated with signal 15
[+29.13s] DEBUG: Session 5480 failed during authentication
[+29.13s] DEBUG: Authenticate result for user crush: Authentication stopped before completion
[+29.17s] DEBUG: Session 5413 exited with return value 0
[+29.17s] DEBUG: Greeter quit
[+29.17s] DEBUG: Sending signal 15 to process 5410
[+29.21s] DEBUG: Process 5410 exited with return value 0
[+29.21s] DEBUG: X server stopped
[+29.21s] DEBUG: Removing X server authority /var/run/lightdm/root/:0
[+29.21s] DEBUG: Releasing VT 7
[+29.21s] DEBUG: Display server stopped
[+29.21s] DEBUG: Display stopped
[+29.21s] DEBUG: Seat stopped
[+29.21s] DEBUG: Display manager stopped
[+29.21s] DEBUG: Stopping daemon
[+29.22s] DEBUG: Exiting with return value 0
```

x-0-greeter.log

```
** (process:5442): WARNING **: unity-greeter.vala:808: Error starting the at-spi registry: Failed to execute child process "/usr/lib/at-spi2-core/at-spi-bus-launcher" (No such file or directory)
[+0.00s] DEBUG: unity-greeter.vala:816: Starting unity-greeter 0.2.8 UID=116 LANG=en_US.UTF-8
[+0.00s] DEBUG: unity-greeter.vala:819: Setting cursor
[+0.00s] DEBUG: unity-greeter.vala:823: Creating background surface
[+0.00s] DEBUG: unity-greeter.vala:826: Loading command line options
[+0.00s] DEBUG: unity-greeter.vala:854: Setting GTK+ settings
[+0.02s] WARNING: Theme parsing error: gtk.css:17:45: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:18:45: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:19:43: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:20:43: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:21:52: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:22:52: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:24:51: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:25:51: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:27:52: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:28:52: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:29:42: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:31:59: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:32:59: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:34:58: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:35:58: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:37:49: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:38:49: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:39:49: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:41:44: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:42:55: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:43:58: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:44:58: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:46:52: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:47:52: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:50:48: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:51:49: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:53:47: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:54:51: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:56:62: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:57:62: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:58:56: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:60:58: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:62:50: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:63:51: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:64:51: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:65:51: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:67:49: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:68:52: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:70:56: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:72:67: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:74:48: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:76:61: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:77:61: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:79:46: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:80:46: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:82:40: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:84:53: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:85:53: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:88:52: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:90:39: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:91:42: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:92:40: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:93:42: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:104:47: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:105:47: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:106:56: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:107:56: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:109:44: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:110:44: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:112:53: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:113:53: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:115:41: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk.css:116:41: Expected ',' in color definition
[+0.02s] WARNING: Theme parsing error: gtk-widgets.css:19:14: Not using units is deprecated. Assuming 'px'.
[+0.02s] WARNING: Theme parsing error: gtk-widgets.css:63:21: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:117:15: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:120:19: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:121:20: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:153:20: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:163:14: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:186:36: Junk at end of value
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:188:19: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:189:20: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:203:14: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:216:20: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:228:20: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:240:14: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:305:19: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:306:20: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:337:19: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:338:20: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:348:14: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:354:19: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:367:18: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:368:20: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:376:14: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:398:19: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:432:14: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:432:16: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:475:19: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:487:19: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:488:20: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:499:20: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:507:20: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:516:20: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:524:20: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:545:44: Expected ')' in color definition
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:567:20: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:579:14: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:627:14: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:642:14: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:647:19: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:650:14: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:659:19: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:683:22: Not using units is deprecated. Assuming 'px'.
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:712:32: Junk at end of value
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:718:32: Junk at end of value
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:723:36: Junk at end of value
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:728:36: Junk at end of value
[+0.04s] WARNING: Theme parsing error: gtk-widgets.css:771:56: Error opening file: No such file or directory
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:802:14: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:845:14: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:867:20: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:868:19: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:882:20: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:883:19: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:899:20: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:900:19: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:915:19: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:916:20: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:928:19: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:929:20: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:940:20: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:952:19: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:959:14: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:963:20: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:964:19: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:973:14: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:977:20: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:978:19: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:989:14: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:993:20: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:994:19: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1011:19: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1012:20: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1021:19: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1022:20: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1044:20: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1063:20: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1077:20: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1099:20: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1116:20: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1131:20: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1145:20: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1155:14: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1164:20: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1170:20: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1178:20: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1193:19: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1265:14: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1314:36: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1323:47: Junk at end of value
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1341:40: Junk at end of value
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1342:52: Missing opening bracket in color definition
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1349:52: Missing opening bracket in color definition
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1350:40: Junk at end of value
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1356:20: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1359:14: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1367:66: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1382:47: Junk at end of value
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1383:36: Junk at end of value
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1395:26: Junk at end of value
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1403:40: Junk at end of value
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1404:29: Junk at end of value
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1412:41: Junk at end of value
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1413:30: Junk at end of value
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1421:38: Junk at end of value
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1422:27: Junk at end of value
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1426:32: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1470:31: Junk at end of value
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1480:36: Junk at end of value
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1503:19: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1504:31: Junk at end of value
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1518:19: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1519:40: Junk at end of value
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1532:19: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1533:40: Junk at end of value
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1550:31: Junk at end of value
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1555:42: Junk at end of value
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:1560:31: Junk at end of value
[+0.06s] DEBUG: unity-greeter.vala:877: Creating Unity Greeter
[+0.06s] DEBUG: Connecting to display manager...
[+0.06s] DEBUG: Wrote 17 bytes to daemon
[+0.06s] DEBUG: Read 8 bytes from daemon
[+0.06s] DEBUG: Read 120 bytes from daemon
[+0.06s] DEBUG: Connected version=1.2.1 default-session=ubuntu show-manual-login=false hide-users=false has-guest-account=true
[+0.08s] WARNING: unity-greeter.vala:130: Failed to load state from /var/lib/lightdm/.cache/unity-greeter/state: Key file contains line '' which is not a key-value pair, group, or comment

[+0.10s] DEBUG: menubar.vala:318: LANG=en_US.UTF-8 LANGUAGE=(null)
[+0.10s] CRITICAL: g_error_free: assertion `error != NULL' failed
[+0.11s] DEBUG: get entries
[+0.11s] DEBUG: menubar.vala:511: Adding indicator object 0x24d5078 at position 0
[+0.11s] DEBUG: Evaluating bitmask for '%l:%M %p'
[+0.11s] DEBUG: Checking against 2 possible times
[+0.12s] DEBUG: Guessing max time width: 62
[+0.12s] DEBUG: get entries
[+0.12s] DEBUG: menubar.vala:511: Adding indicator object 0x254c178 at position 1
[+0.12s] WARNING: IndicatorObject class does not have an accessible description.
[+0.12s] WARNING: IndicatorObject class does not have an accessible description.
[+0.12s] DEBUG: get entries
[+0.12s] DEBUG: get entries
[+0.12s] DEBUG: menubar.vala:511: Adding indicator object 0x24c26d8 at position 2
[+0.12s] DEBUG: menubar.vala:335: LANG=en_US.UTF-8 LANGUAGE=(null)
[+0.12s] DEBUG: Loaded session /usr/share/xsessions/gnome-fallback.desktop (GNOME Classic (No effects), This session logs you into GNOME with the traditional panel without any graphical effect.)
[+0.12s] DEBUG: Loaded session /usr/share/xsessions/ubuntu-2d.desktop (Ubuntu 2D, This session logs you into Ubuntu 2D Mode)
[+0.12s] DEBUG: Loaded session /usr/share/xsessions/cairo-dock-fallback.desktop (Cairo-Dock (Gnome No effects), This session logs you into GNOME with Cairo-Dock and without any graphical effect.)
[+0.12s] DEBUG: Loaded session /usr/share/xsessions/cairo-dock-unity.desktop (Cairo-Dock (with Unity Panel), This session logs you into GNOME with Cairo-Dock and Unity-2D panel)
[+0.12s] DEBUG: Loaded session /usr/share/xsessions/gnome-shell.desktop (GNOME, This session logs you into GNOME)
[+0.12s] DEBUG: Loaded session /usr/share/xsessions/cairo-dock.desktop (Cairo-Dock (Gnome + Effects), This session logs you into GNOME with Cairo-Dock and with graphical effects.)
[+0.12s] DEBUG: Ignoring session /usr/share/xsessions/gnome.desktop
[+0.12s] DEBUG: Loaded session /usr/share/xsessions/xterm.desktop (Recovery Console, Failsafe session with only xterm)
[+0.12s] DEBUG: Loaded session /usr/share/xsessions/ubuntu.desktop (Ubuntu, This session logs you into Ubuntu)
[+0.12s] DEBUG: Loaded session /usr/share/xsessions/xsession.desktop (User Defined Session, Custom ~/.xsession script)
[+0.12s] DEBUG: Loaded session /usr/share/xsessions/gnome-classic.desktop (GNOME Classic, This session logs you into GNOME with the traditional panel)
[+0.12s] DEBUG: session-chooser.vala:42: Adding session cairo-dock (Cairo-Dock (Gnome + Effects))
[+0.12s] DEBUG: session-chooser.vala:42: Adding session cairo-dock-fallback (Cairo-Dock (Gnome No effects))
[+0.12s] DEBUG: session-chooser.vala:42: Adding session cairo-dock-unity (Cairo-Dock (with Unity Panel))
[+0.13s] DEBUG: session-chooser.vala:42: Adding session gnome-shell (GNOME)
[+0.13s] DEBUG: session-chooser.vala:42: Adding session gnome-classic (GNOME Classic)
[+0.13s] DEBUG: session-chooser.vala:42: Adding session gnome-fallback (GNOME Classic (No effects))
[+0.13s] DEBUG: session-chooser.vala:42: Adding session xterm (Recovery Console)
[+0.13s] DEBUG: session-chooser.vala:42: Adding session ubuntu (Ubuntu)
[+0.13s] DEBUG: session-chooser.vala:42: Adding session ubuntu-2d (Ubuntu 2D)
[+0.13s] DEBUG: session-chooser.vala:42: Adding session xsession (User Defined Session)
[+0.22s] DEBUG: Setting keyboard layout to 'us'
[+0.25s] DEBUG: main-window.vala:98: Screen is 2800x900 pixels
[+0.25s] DEBUG: main-window.vala:104: Monitor 0 is 1360x768 pixels at 0,0
[+0.25s] DEBUG: main-window.vala:104: Monitor 1 is 1440x900 pixels at 1360,0
[+0.25s] DEBUG: Loading users from org.freedesktop.Accounts
[+0.25s] DEBUG: Loading user /org/freedesktop/Accounts/User1000
[+0.26s] DEBUG: Loading user /org/freedesktop/Accounts/User1001
[+0.26s] DEBUG: Loading sessions from org.freedesktop.DisplayManager
[+0.26s] DEBUG: unity-greeter.vala:327: Adding/updating user crush (Crush)
[+0.26s] DEBUG: unity-greeter.vala:327: Adding/updating user temp (Temp)
[+0.26s] DEBUG: unity-greeter.vala:184: Adding guest account entry
[+0.32s] DEBUG: unity-greeter.vala:496: Failed to write state: Error writing to file: Bad address
[+0.32s] DEBUG: Starting authentication for user crush...
[+0.32s] DEBUG: Wrote 21 bytes to daemon
[+0.32s] DEBUG: unity-greeter.vala:880: Showing greeter
[+0.32s] DEBUG: unity-greeter.vala:352: Showing main window
[+0.32s] DEBUG: New style for time label
[+0.32s] DEBUG: Evaluating bitmask for '%l:%M %p'
[+0.32s] DEBUG: Checking against 2 possible times
[+0.32s] DEBUG: Guessing max time width: 62
[+0.34s] DEBUG: background.vala:315: Regenerating backgrounds
[+0.34s] DEBUG: background.vala:67: Making background /usr/share/backgrounds/Ubuntu-Wallpaper-Images.png at 1360x768,1440x900
[+0.34s] DEBUG: New style for time label
[+0.34s] DEBUG: Evaluating bitmask for '%l:%M %p'
[+0.34s] DEBUG: Checking against 2 possible times
[+0.34s] DEBUG: Guessing max time width: 62
[+0.34s] DEBUG: unity-greeter.vala:893: Starting main loop
[+0.34s] DEBUG: Read 8 bytes from daemon
[+0.34s] DEBUG: Read 35 bytes from daemon
[+0.34s] DEBUG: Prompt user with 1 message(s)
[+0.37s] WARNING: Getting layout failed: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `com.canonical.dbusmenu' on object at path /com/canonical/indicator/users/menu
[+0.37s] DEBUG: Num devices: '0'

[+0.37s] MESSAGE: Couldn't find primary device
[+0.37s] DEBUG: Num devices: '0'

[+0.37s] DEBUG: icon_policy is: 0 (present==0, charge==1, never==2)
[+0.37s] DEBUG: count_batteries found 0 batteries (0 are charging/discharging)
[+0.37s] DEBUG: should_be_visible: no
[+0.37s] DEBUG: menubar.vala:519: Removing indicator object 0x24c2558
[+0.37s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+0.37s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+0.37s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+0.37s] WARNING: menubar.vala:531: Indicator object 0x24c2558 not in menubar
[+0.37s] DEBUG: notify visible signal received
[+0.37s] CRITICAL: ido_calendar_menu_item_set_date: assertion `IDO_IS_CALENDAR_MENU_ITEM(menuitem)' failed
[+0.37s] DEBUG: unity-greeter.vala:310: starting system-ready sound
[+0.38s] DEBUG: New calendar item
[+0.38s] DEBUG: indicator-sound: new_volume_slider_widget
[+0.38s] DEBUG: indicator-sound: new_voip_slider_widget
[+0.47s] DEBUG: background.vala:116: Render of background /usr/share/backgrounds/Ubuntu-Wallpaper-Images.png complete
[+0.54s] DEBUG: background.vala:67: Making background /home/crush/Pictures/mthighwestA.png at 1360x768,1440x900
[+0.70s] DEBUG: Setting keyboard layout to 'us'
[+2.42s] DEBUG: background.vala:116: Render of background /home/crush/Pictures/mthighwestA.png complete

```

---

### Post by einstein**-7 on 2013-02-04
This was the result of one login attempt with unity-greeter.

---

### Post by einstein**-7 on 2013-02-05
Solved this issue for everyone in the future with the
```
sudo chown  -R  $USER:$USER  $HOME
```
presto! works

---

