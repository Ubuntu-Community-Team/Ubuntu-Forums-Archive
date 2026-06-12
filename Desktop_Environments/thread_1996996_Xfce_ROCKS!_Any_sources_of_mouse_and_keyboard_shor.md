---
title: "Xfce ROCKS! Any sources of mouse and keyboard shortcuts please?"
date: 2012-06-04
forum: Desktop Environments
---

### Post by blackbird34 on 2012-06-04
The title sums it up really. I love Xfce, i am in the process of settling in, it seems rock solid and loveable, exactly right for my crappy lappy:guitar:

SO after adding my all time favourite SYNAPSE for quick app search, could anyone tell me of a few sources of handy keyboard shortcuts? And most of all, is it possible to configure mouse shortcuts and swipes etc to rival a mac (switching workspaces, toggling fullscreen, etc) and which utility would be needed?

Thanks all):P

---

### Post by 3Miro on 2012-06-04
From Apps -> Settings -> Mouse/Keyboard/Windows Manager, you can adjust a lot of shortcuts for the keyboard and mouse. 

App shortcuts will let you execute any command with a keyboard shortcut, i.e. raise/lower volume, pause/play media, start browsers/file manager/terminal/etc.

From Window Manager you can adjust the shortcuts for maximize/minimize, move windows, close windows, navigate through Workspaces.

From Windows Manager Tweaks, you can also enable Workspace switching by scrolling the mouse wheel over the desktop.

By default, XFCE doesn't have mouse gestures, you will have to look for a 3d party app for that and I don't know of any.

---

### Post by LewisTM on 2012-06-05
You can use Easystroke to configure mouse gestures for Linux.

Brightside is also useful to bind screen corners to actions. It's sometimes used with *xdotool* to invoke window manager actions that can only be accessed through keyboard shortcuts. Run *brightside-properties* to configure.

For example
```
xdotool key Alt+F11
```
Could be associated with the top right corner to bring the current window fullscreen.

Another useful tool is wmctrl. For instance:
```
wmctrl -a Thunderbird
```
Could be associated with another corner to switch to Thunderbird wherever you are and switch desktop if necessary. Very handy when receiving emails.
```
wmctrl -r Thunderbird -b toggle,fullscreen
```
Will toggle Thunderbird fullscreen a bit like the first example.

Enjoy!

---

### Post by blackbird34 on 2012-06-05
Thanks everyone!!

---

