---
title: "Switched from Ubuntu to Xubuntu: apps keep auto-starting"
date: 2006-09-24
forum: Desktop Environments
---

### Post by kblood on 2006-09-24
Hello everyone,

I have a computer that is fast enough to run Gnome nicely, but I wanted to try XFCE, and I really like it. It has more than enough eye-candy, but I mostly enjoy the extra "snappiness" it has. Anybody appreciates a little extra responsiveness.

Ok, here is my problem: I had a couple of programs autostarting in Ubuntu, but I don't want them anymore in Xubuntu (checkgmail and Glipper, both of which can be substituted by native XFCE panel applets).
I have looked around like crazy, but I can't find where they are being started.
I found some files inside the .config/autostart folder which seemed to have to do with auto-starting the applications, so I edited them to "X-GNOME-Autostart-enabled=false".
They still autostart when I log in.

Any ideas? The XFCE session manager doesn't give me an option to alter autostart apps, and the option to start Gnome services is disabled.

Thanks!

---

### Post by whizbaby on 2006-09-24
Have you tried to close all applications and *remember session* when you logout (there's a box you can check)?

---

### Post by kblood on 2006-09-24
Yes, no change. I have been running Xubuntu exclusively the last week, and I have rebooted several times, and several of them with the checkbox activated to remember the session.

But as soon as I am done with something that prevents me from doing it, I'll do it again, just in case.

---

### Post by whizbaby on 2006-09-24
> **kblood said:**
>  I have rebooted several times
You don't have to reboot all the time, logout and then login again is enough (the programs are started at login, not boot time).

---

### Post by kblood on 2006-09-24
> **whizbaby said:**
> You don't have to reboot all the time, logout and then login again is enough (the programs are started at login, not boot time).

Yes, I know. What I meant with that was that in the days that I have been using Xubuntu I have already rebooted my computer (not specifically to test it, just through normal usage) and it made no difference.

Just in case, though, I just logged out and logged back in, with the "Save session" check activated, and as usual, Glipper and checkgmail got started.

---

### Post by aysiu on 2006-09-24
How about *not* saving your session?

---

### Post by kblood on 2006-09-24
> **aysiu said:**
> How about *not* saving your session?

I think you think that I'm *not* closing those two apps before logging out :D 
I do, I close them right away as soon as I log in, so when I log out they are closed already a long time.

In any case, I will give that a try.

---

### Post by whizbaby on 2006-09-24
Can you post the output of
**ls -la /etc/xdg/autostart/**
?

---

### Post by kblood on 2006-09-24
I just tried logging out, deactivating the "Save session" checkbox, and logging back in. Same result, both applications start up.

Here is the output of "ls -la /etc/xdg/autostart/":
```
total 28
drwxr-xr-x 2 root root 4096 2006-07-31 13:01 .
drwxr-xr-x 9 root root 4096 2006-09-17 12:53 ..
-rw-r--r-- 1 root root  297 2006-05-21 07:39 beagled.desktop
-rw-r--r-- 1 root root 2401 2006-05-29 19:38 gnome-power-manager.desktop
-rw-r--r-- 1 root root 3220 2006-05-16 16:53 gnome-volume-manager.desktop
-rw-r--r-- 1 root root  335 2006-05-18 09:36 nm-applet.desktop
-rw-r--r-- 1 root root  236 2006-05-26 17:40 update-notifier.desktop

```

---

### Post by whizbaby on 2006-09-24
Humm, it's not started there (though I don't know nm-applet, what is this?), do you have a .xsession or .Xsession file in your homedir?

---

### Post by kblood on 2006-09-24
nm-applet is, I think, the Gnome Network Manager applet. I don't use it, so I don't know how it got there.

No, no .xsession or .Xsession files in my homedir.

---

### Post by whizbaby on 2006-09-24
Tried to log into gnome and remove it there?

---

### Post by kblood on 2006-09-24
I guess I will have to. Still, I would rather find out where these apps are getting triggered.

---

### Post by kblood on 2006-09-24
Ok, found it and solved it.

It was the .desktop files in .config/autostart/
They have a setting: X-GNOME-Autostart-enabled=(true or false)
It seems that XFCE, regardless of that setting being true or false, starts them up.
I checked which one belonged to the applications I was looking for, and removed them. Logged out, back in, and it's solved.

Sorry for wasting your time, but I guess we've all learnt a bit today :)

---

### Post by whizbaby on 2006-09-24
> **kblood said:**
> Sorry for wasting your time, but I guess we've all learnt a bit today :)
Yo

---

