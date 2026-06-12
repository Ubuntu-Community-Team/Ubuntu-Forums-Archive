---
title: "[SOLVED] AWN problems"
date: 2008-08-03
forum: Desktop Environments
---

### Post by enazguy on 2008-08-03
I recently installed an apple dock. Its called AWN. As I added more launchers, it had a thin white line near the end of the dock. I ran it in the terminal and this is what i got.

~$ avant-window-navigator &
[1] 9431
zanemilbourn@zanemilbourn-laptop:~$ Screen is composited.
APPLET : /usr/lib/awn/applets/taskman.desktop
APPLET : /home/zanemilbourn/.config/awn/applets/python-test.desktop.in.in
Traceback (most recent call last):
  File "/home/zanemilbourn/.config/awn/applets/battery-applet/battery-applet.py", line 25, in <module>
    import awn
ImportError: No module named awn



What should I do?

---

### Post by enazguy on 2008-08-03
I deleted a battery applet which was causing the white line.

---

