---
title: "Inspiron 1420N external monitor display not sleeping"
date: 2007-07-31
forum: Dell  Ubuntu Support
---

### Post by robertbub on 2007-07-31
My external monitor works well, but I have one problem.  The display never goes to standby and I must shut the monitor off by hand.

I went through [http://www.berthon.eu/wiki/foss:ubuntu:wikishelf:hal:feisty](http://www.berthon.eu/wiki/foss:ubuntu:wikishelf:hal:feisty)  and have verified that the dcdbas module is loaded, but it still doesn't work.

Via Preferences->Screensaver->Power Management->"Put display to sleep when inactive for", I set it to 15 minutes.  I also disabled "Activate screensaver when computer is idle", as suggested.

Does anyone have a suggestion on how to fix this?

---

### Post by apswartz on 2007-07-31
Sorry. I haven't tried an external monitor on the Dell 1420 yet, but I hope to soon, so I am interested in seeing if you get any help. Good luck.

---

### Post by robertbub on 2008-03-15
So, I tried

```
gnome-screensaver-command --exit
gnome-screensaver --no-daemon --debug
```

and what I see is:

```
[_gs_watcher_notice_window_created] gs-watcher-x11.c:568 (09:43:34):     Window created: noticing activity on 0x304D715
[_gs_watcher_notice_window_created] gs-watcher-x11.c:568 (09:43:34):     Window created: noticing activity on 0x135030C
[_gs_watcher_notice_window_created] gs-watcher-x11.c:568 (09:43:34):     Window created: noticing activity on 0x135030F
```

ad infinitum, even if I never touch the mouse nor the keyboard.  So, I can only assume that this is a problem with gs-watcher-x11 interacting with an external keyboard, mouse, or display.

Oddly, both workrave and RSIbreak correctly detect key presses and mouse movements correctly.  So, this must be an innate bug in gs-watcher-x11.

Still no progress...:cry:

---

### Post by robertbub on 2008-03-15
Ah, I just discovered that if I start the screensaver on the command line (*gnome-screensaver*) after logging in, killing it(*gnome-screensaver-command --exit*), it successfully goes into screen saver mode.  (Unfortunately, it doesn't seem to use the power-saving features.)

Weird.

---

