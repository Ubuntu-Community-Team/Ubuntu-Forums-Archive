---
title: "Compiz Fusion Screenlets won't work"
date: 2007-08-17
forum: Desktop Effects &amp; Customization
---

### Post by Solvax on 2007-08-17
I installed compiz fusion yesterday, after that i installed the widgets plugin,
I enabled this plugin on the compizconfig settings manager... (checked the box)
Now i downloaded the screenlets ver0.0.9 from compiz fusion forums and
followed the steps:

[http://forum.compiz-fusion.org/showthread.php?t=323](http://forum.compiz-fusion.org/showthread.php?t=323)

I unpacked the tarball, entered the terminal, browsed to the unpacked folder and then used
the command sudo make install, after that sudo make menu.
I made the install, I made the menu, now the screenlets menu appears correctly,
but the screenlets simply don't work, when i click on one nothing happens.

I hope someone can help me out...

Greetz

~Solvax

---

### Post by Solvax on 2007-08-17
BUMP, anyone got a solution for my problem?
I know there must be a smartass somewhere out there who can help me :)
If you have an idea what i should do, please tell me.

~Solvax

---

### Post by FuturePilot on 2007-08-17
I think it's a problem with the latest version of screenlets. I remember seeing it somewhere that the widget plugin no longer works correctly with screenlets 0.9

---

### Post by Solvax on 2007-08-17
Thanks a lot for your feedback!
Do you think i should try an older screenletversion?
Like 7.0 or 8.0 ?


Maybe this helps:
The output from the terminal when i try to launch the Clock screenlet
> root@Solvaxonline38a1:~# /usr/local/share/screenlets/Clock/ClockScreenlet.py
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:69: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
CachingBackend: Loading instances from cache
Traceback (most recent call last):
  File "/usr/local/share/screenlets/Clock/ClockScreenlet.py", line 433, in <module>
    screenlets.session.create_session(ClockScreenlet)
  File "/usr/lib/python2.5/site-packages/screenlets/session.py", line 301, in create_session
    session.start()
  File "/usr/lib/python2.5/site-packages/screenlets/session.py", line 150, in start
    if services.service_is_running(sln):
  File "/usr/lib/python2.5/site-packages/screenlets/services.py", line 155, in service_is_running
    bus = dbus.SessionBus()
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 669, in __new__
    mainloop=mainloop)
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 293, in __new__
    mainloop=mainloop)
dbus.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
root@Solvaxonline38a1:~# 



~Solvax

---

### Post by FuturePilot on 2007-08-17
You could try going back to 0.7. I've seen those errors before. Usually happens when you try to launch a screenlet that was made for 0.7 in 0.9. Try adding the clock from Applications>Accessories>Screenlets

---

### Post by AlexenderReez on 2007-08-17
i can launch any screenlets application but i don't have screenlets-tray in 9.0 version:confused::confused:

---

### Post by Depressed Man on 2007-08-17
I don't think there's a screenlets-tray anymore in .9

---

### Post by FuturePilot on 2007-08-17
No, there is no more screenlets-tray.

---

### Post by AlexenderReez on 2007-08-17
then how can we control screenlets if there is no screenlets-tray ?

---

### Post by FuturePilot on 2007-08-17
Either use the little screenlets control panel, Applications>Accessories>Screenlets or you'll have to run them individually. Usually like ```
/usr/local/share/screenlets/screenlet/screenlet.py
```

---

### Post by AlexenderReez on 2007-08-17
> **FuturePilot said:**
> Either use the little screenlets control panel, Applications>Accessories>Screenlets or you'll have to run them individually. Usually like ```
/usr/local/share/screenlets/screenlet/screenlet.py
```

i don't have that -->

> reez@aLeXeNdeRreEz:~$ /usr/local/share/screenlets/screenlet/screenlet.py
bash: /usr/local/share/screenlets/screenlet/screenlet.py: No such file or directory


---

### Post by kbzona on 2007-08-18
Why whenever i try to run a screenlet within a shortcut outside his folder it doesnt works but if i run it within his folder it works???? also the same happens when i try running it in a console...

---

### Post by FuturePilot on 2007-08-18
> **AlexenderReez said:**
> i don't have that -->

That was just an example I made up. You'll have to substitute the screenlet name. Here try this one. It's a real one this time :p
```
/usr/local/share/screenlets/Picframe/PicframeScreenlet.py
```

---

### Post by Solvax on 2007-08-20
i'm now using version 0.1.0, and that works perfectly with the manager!
Thank you all for helping

---

### Post by Sunflower1970 on 2007-08-20
Been struggling with these most of the evening here. Does anyone have an earlier version of screenlets? (0.0.7 or earlier. I have 0.0.9 in my archives, but that one gave me some trouble, too) The temperature gague no longer works, nor the CPU monitor. It's way off. And my clock is gone. Tried starting it a few different times, different ways, and it just won't start. (about the only thing that works is the flower...and it's growing quite nicely :))

---

### Post by XTREEM|RAGE on 2007-08-21
> **Sunflower1970 said:**
> Been struggling with these most of the evening here. Does anyone have an earlier version of screenlets? (0.0.7 or earlier. I have 0.0.9 in my archives, but that one gave me some trouble, too) The temperature gague no longer works, nor the CPU monitor. It's way off. And my clock is gone. Tried starting it a few different times, different ways, and it just won't start. (about the only thing that works is the flower...and it's growing quite nicely :))

> **Solvax said:**
> i'm now using version 0.1.0, and that works perfectly with the manager!
Thank you all for helping

Version 0.1.0 is already out, try to use that 1 ;'D

---

### Post by Sunflower1970 on 2007-08-21
Ahh. nevermind. I figured the whole thing out.. (after a few screaming matches with my laptop...I won :D )

---

