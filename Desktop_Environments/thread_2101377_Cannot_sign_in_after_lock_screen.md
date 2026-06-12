---
title: "Cannot sign in after lock screen"
date: 2013-01-04
forum: Desktop Environments
---

### Post by Kaninepete on 2013-01-04
Sometimes, after locking the screen, or hibernating, I am unable to type in the password box, and therefore unable to sign back in.

Could it be because I'm using cinnamon? It didn't start immediately when I installed, but rather some time later.

I've found a workaround by clicking switch user, and signing in from there. 
But sometimes this workaround results in an unresponsive black screen.
At this point even ctrl-alt-1 doesn't work, and I am forced to shut down and lose all unsaved work (as far as I know.)

I have not found any way to predict when this will happen, and I'm terrified to start any long renders now for fear of losing them.

Can anyone advise me on how to fix this?

---

### Post by beerthirty on 2013-07-01
I been seeing this problem as well, minus the black screen part.  It's been more of an annoyance than anything.

I am seeing lots of these in the auth.log when I am not using my machine:
```

Jun 30 08:13:22 U-Box dbus[1215]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.58" (uid=1000 pid=2937 comm="/usr/lib/indicator-session/indicator-session-servi") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.16" (uid=0 pid=2004 comm="/usr/sbin/console-kit-daemon --no-daemon ")

```

I am seeing this in the syslog when I switch users to log back in:

```
Jul 1 09:33:57 U-Box acpid: client connected from 8824[0:0]
Jul 1 09:33:57 U-Box acpid: 1 client rule loaded
Jul 1 09:33:58 U-Box acpid: client 1604[0:0] has disconnected
Jul 1 09:33:58 U-Box acpid: client 1604[0:0] has disconnected
Jul 1 09:33:58 U-Box acpid: client connected from 8824[0:0]
Jul 1 09:33:58 U-Box acpid: 1 client rule loaded
Jul 1 09:33:58 U-Box dbus[1215]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Jul 1 09:33:58 U-Box dbus[1215]: [system] Successfully activated service 'org.freedesktop.systemd1'
 
```

It seems like the desktop session is in tact after pressing the switch users button on the lock screen and logging back in.
Did you ever find a fix for you problem?

B30

---

### Post by godric7gt on 2013-09-25
I am facing this problem too. I type the password to unlock the system, except that no text gets reflected, it remains blank, I can switch user, but once I type the password at the login screen, I get a messed up screen! Does anyone know if there is a bug listed for this? or perhaps a workaround?

---

