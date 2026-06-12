---
title: "message to xfce user from admin via ssh"
date: 2013-03-05
forum: Desktop Environments
---

### Post by trappo on 2013-03-05
I often connect via ssh to the computer of a friend of mine for system upgrades and administration because he doesn't like to take care of it.
He has a very slow machine and sometimes it coud be useful sending him messages like "i'm upgrading - don't worry - the system will be very slow for a while"
Is there a simple way to show messages or notifications from the command line to the desktop used by another user?

---

### Post by Cheesemill on 2013-03-05
```
DISPLAY=:0 notify-send "System is being updated"
```

If you are using the terminal on a local machine then you can just use the notify-send command. As you are connecting remotely via ssh then your session doesn't have a display associated with it, hence the need to prepend the command with DISPLAY=:0 so it knows which display to send the notification to.

Take a look at the man page for notify-send, there are other options you can use such as the severity of the notification and how long it is displayed for.

---

