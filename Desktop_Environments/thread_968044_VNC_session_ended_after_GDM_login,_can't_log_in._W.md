---
title: "VNC session ended after GDM login, can't log in. What'd I do wrong?"
date: 2008-11-02
forum: Desktop Environments
---

### Post by beowulfshaeffer on 2008-11-02
Ok, so, I had VNC set up under 8.04 so that I could VNC into the login screen and log in. Well, I thought I made the right changes to 8.10 but I missed something. Now I enter my UN and password, and then the VNC session ends, and I can see on the box's monitor that it goes back to the login screen. What have I done wrong? :confused:

I have:
```
/usr/bin/x11vnc -rfbauth /root/.vnc/passwd -o /tmp/x11vnc.log -forever -bg -rfbport 5900
```
in the /etc/gdm/Init/Default file, and
```
KillInitClients=false
```
in my /etc/gdm/gdm.conf file.

---

### Post by krunge on 2008-11-02
> **beowulfshaeffer said:**
> Ok, so, I had VNC set up under 8.04 so that I could VNC into the login screen and log in. Well, I thought I made the right changes to 8.10 but I missed something. Now I enter my UN and password, and then the VNC session ends, and I can see on the box's monitor that it goes back to the login screen. What have I done wrong?

The following thread is working on the same problem it appears:

[http://ubuntuforums.org/showthread.php?t=965695&highlight=x11vnc](http://ubuntuforums.org/showthread.php?t=965695&highlight=x11vnc)

Have a look at the various log files and post if you find any useful messages.

---

### Post by Skip Da Shu on 2009-01-05
And... the fix is in the above quoted thread!

---

