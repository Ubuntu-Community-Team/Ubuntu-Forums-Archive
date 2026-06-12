---
title: "window snap to 3rd"
date: 2023-06-27
forum: Desktop Environments
---

### Post by ant2ne on 2023-06-27
using xubuntu. If I drag a window to the edge, it snaps to half the screen. This is great as I have an ultra wide. So I get 2 windows like   [    ][    ]  but I'd really like it to snap to in thirds, like [   ][   ][   ], or even better like [   ][ ][   ], with a terminal in the middle. How can I do this? Is there an app for that?

thanks?

---

### Post by TheFu on 2023-06-28
Proper X/Windows applications support the -geometry option which lets us specify the size and location for a window to be displayed. If a window doesn't support that option, there's always xdotool.  Use the *windowmove x y*  and  *windowsize x y *  suboptions to move and resize the window after the program is launched.
For example, 
```
xdotool set_desktop_viewport 1980 0
xdotool search --name "Mozilla Firefox" windowmove 170  0
xdotool search --name "Mozilla Firefox" windowsize 1600  815
xterm -geometry 80x15+0-0 $XTERM_OPTS
```

For Wayland, I haven't any clue.  ydotool is supposed to have many features of xdotool, but some that I need are missing, so I haven't touched Wayland.

---

