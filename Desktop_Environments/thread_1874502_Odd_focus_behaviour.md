---
title: "Odd focus behaviour"
date: 2011-11-03
forum: Desktop Environments
---

### Post by agnul on 2011-11-03
I'm experiencing some odd window focus behaviour on 11.10/unity, and I'm not sure this comes from the standard configuration or me playing around with "focus-follows-mouse".

For starters: let's say I have a terminal overlapping Firefox's window, focus is on the terminal. If I move the cursor outside of the terminal on the Firefox window (no click) and play with the scroll-wheel, focus remains on the terminal but Firefox is doing the scrolling. Focus follows mouse is OFF, I can reproduce this 100% of the time.

More puzzling: sometimes when switching between windows on different workspaces (either clicking on the dash or using alt-tab) I get "half focused" windows, for instance I can type inside the terminal but the title bar is in the "unfocused" state and the cursor inside the window is the hollow one instead of the usual block one. Or I can scroll window contents, switch between tabs on Eclipse but not type. Usually I need to switch away from the application and then back to fix this. Also at times when switching to Firefox I can type in the location bar or search bar, but there's no drop-down for suggestions.

Any idea what may be at miss here? Focus mode is the usual "click to focus", but a couple of days back I played with "sloppy focus" and moved back using gnome-tweak-tool. Maybe some settings have not been switched back?

---

### Post by ajgreeny on 2011-11-03
I can't help with your second focus problem, or even replicate it at all.

The first one, the scrolling in firefox when there is a focused terminal or other window above, is also true in 10.04 which I am running, and I believe it has always been so, but I have no way to check that historically any more.   I find that behaviour very useful sometimes, and more a feature than a problem.

---

### Post by typhoon_tip on 2011-11-03
The first one is not a problem, it is an intende function, because it has been like this since 10.04, then 10.10, 11.04 and finally 11.10, all same behaviour.

The second bug I noticed as well: it's related to the top window title bar, not to "half window". Sometimes it remains semi-transparent even if the window is selected and on top, and sometimes it remain "non-transparent" even if the window is sitting below another window and doesn't have the focus (especially when you have many Skype chat windows opened).

I don't know if anyone has filed a bug yet, I thought it has something to do with some bizzare settings due to upgrade.

Did you do a _fresh install_ of 11.10 ?

---

### Post by agnul on 2011-11-03
Yup, in my case it was a fresh install.

(Wow, I've been running 10.10 for over a year and never noticed the scrollwheel thing.)

---

### Post by typhoon_tip on 2011-11-03
> **agnul said:**
> (Wow, I've been running 10.10 for over a year and never noticed the scrollwheel thing.)

:D

OK then, I will file a bug. Since it will be most probably put in wishlist (but not sure indeed, because aestetical is taken more seriously these days with Unity), we need to raise the heat to make it being "considered". To me personally is quite annoying, as I tend to be a perfectionist with my desktop look. After I opened the bug, I will post the link here, please login to Launchpad and click "This bug affects me", so we have multiple users to start with.

:popcorn:

---

### Post by typhoon_tip on 2011-11-03
OK done.

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/885941](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/885941)

Please login in Launchpad (or create an account if you haven't) and click "this bug affects me". Confirm that is the same behaviour by viewing my screenshot attachment there.

---

### Post by agnul on 2011-11-04
I think I've managed to reproduce the Firefox issue.

[LIST=1]
[*]Open Firefox
[*]Switch from Firefox to an application in a different workspace by clicking on the application's icon in the dash
[*]Switch back to Firefox clicking on the icon in the dash and move quickly the mouse away from the dash
[*]Start typing in Firefox's awesome bar
[/LIST]
the awesome bar has focus, text appears but no suggestions drop down appears.

Switching away from Firefox and back using Alt-Tab and everything is fine again.

---

### Post by typhoon_tip on 2011-11-04
This might be solely related to Firefox. In Chrome there are no problems like this.

---

### Post by typhoon_tip on 2011-11-04
I have added another note in the bug, the behaviour is very bad when you use the "scale" plugin:

> Add one more note. The behaviour is very bad when you open multiple window of the same app, then you use the launcher to open the "Scale windows" selector (for example, if you have 3 windows it will show all of them maximized, and mouse-over them will highlight the title bar). Sometimes the title bar appear cut, erratic, sometimes disappear totally. Sometimes does not appear at all, especially if the window is maximized.

Scale plugin used to work perfectly on 10.04, 10.10 and 11.04. I always used it in combination with active corners (show windows and show desktops active corner commands, setup with Ubuntu Tweaks).

---

### Post by typhoon_tip on 2011-11-11
Bump, this is now a confirmed bug and is quite annoying when you want to "show off" your nice Desktop to some other people:
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/885941](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/885941)

Can anyone confirm that LiveCD 11.10 has the same problem as my last screen-shot attached to the bug ? To replicate the bug, simply:

- Open two nautilus window
- Move one window off the edge of the screen for about half size
- Click Unity launcher icon to start the scale window plugin, and see if you get the same effect

This bug of window decoration shows itself in many different ways, this is one of them.

---

### Post by agnul on 2011-11-14
Actually I haven't noticed any transparency weirdness (I'm using a modified ambiance theme), but I've been experiencing some odd behaviour with empathy: [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/887025](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/887025)

---

### Post by typhoon_tip on 2011-11-14
Yeah it might be related. Other guys were noticing that the shade command doesn't work, it leaves an empty window frame behind (still related to unity-window-decorator package or metacity, seems).

---

