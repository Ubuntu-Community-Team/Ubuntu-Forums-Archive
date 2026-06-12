---
title: "This Sucks..."
date: 2009-04-22
forum: General Help
---

### Post by collinge on 2009-04-22
I am using Ubuntu 8.04 and i this error message when i login 

"There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in."

My 3d Cube is gone and AWN will not start.... can anyone help??

---

### Post by Crafty Kisses on 2009-04-22
Try pressing the following:
```
Control+Alt+Backspace
```
If you get a prompt, type the following:
```
startx
```

---

### Post by collinge on 2009-04-22
that does nothing

---

### Post by LateNiteTV on 2009-04-22
try this as root
```
killall -9 trackerd
dbus-launch trackerd
```

---

### Post by collinge on 2009-05-01
Thank you.  I went ahead and upgraded to 9.04 and it corrected the problem.

---

### Post by Yellow Pasque on 2009-05-01
In the future, try and use descriptive thread titles.

---

