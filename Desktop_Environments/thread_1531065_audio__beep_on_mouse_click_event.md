---
title: "audio / beep on mouse click event"
date: 2010-07-14
forum: Desktop Environments
---

### Post by kqr2 on 2010-07-14
Is it possible to configure X11 and/or XFCE to play an audio file or beep the computer speaker when a mouse click event occurs?

This is actually for a touchscreen kiosk setup, however, touchscreen presses look like mouse click events. The goal is to provide audio feedback.

Although I'm using XFCE, anything that generically works would be fine.

I found xfsound, however, it doesn't work with XFCE4.  I downloaded the source, however, it is tightly integrated with the older version of XFCE 3.8

[http://swoolley.org/man.cgi/1/xfsound](http://swoolley.org/man.cgi/1/xfsound)

It basically listens to X11 events and can play sounds accordingly , e.g. when a button press event occurs.

Is there another utility like xfsound that can respond  in a similiar manner?  Or is it possible to configure the x11 input driver evdev in xorg.conf for audio feedback?

---

