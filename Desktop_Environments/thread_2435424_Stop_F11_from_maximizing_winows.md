---
title: "Stop F11 from maximizing winows"
date: 2020-01-20
forum: Desktop Environments
---

### Post by cjsmall on 2020-01-20
I recently upgraded to Xubuntu 19.10 and now F11 has now been automatically assigned to toggle maximize/minimize window.


[B]# xfconf-query -c xfce4-keyboard-shortcuts -lv | grep -i f11
/xfwm4/default/<Alt>F11                    fullscreen_key
[/B]

This shows that Alt-F11 is assigned this task, but Alt-F11 does nothing while F11 does.
I have assigned the following functions in Window Manager --> Keyboard


[B]/xfwm4/custom/<Super>F9                    maximize_vert_key
/xfwm4/custom/<Super>F10                   maximize_horiz_key
/xfwm4/custom/<Super>F12                   maximize_window_key
[/B]

and they all work as expected.  If it's useful, **xev** shows that F11 has a keycode of 95 and keysym of 0xffc8, F11


I  use F11 and Alt-F11 in my editor and for other purposes, so I need to  disable this new window manager function.  There is no F11 assignment  under Window Manager or Keyboard settings.  How can I disable it?


Thanks.

---

### Post by cjsmall on 2020-01-23
I have solved this problem with the help from someone on the Xfce forum.  For anyone else who is also looking for a solution to deactivating F11 in the xfce4-terminals, please see the full discussion here:
[URL="https://forum.xfce.org/viewtopic.php?pid=56226#p56226"]
https://forum.xfce.org/viewtopic.php?pid=56226#p56226[/URL]

---

