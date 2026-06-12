---
title: "Alt key with compiz instantly moves window"
date: 2006-11-04
forum: Desktop Environments
---

### Post by say on 2006-11-04
After installing compiz according to the instructions on the wiki (meaning a rather plain-vanilla-compiz installation) my Alt key seems to be mapped to "move current active window exactly one workspace to the right" (exactly one workspace meaning that if the window is on a corner before the move, it will be on another corner after the move). The "camera" does not follow the window, it stays put.

I can't see this behaviour documented anywhere, and it is quite annoying considering all the compiz shortcuts that involve alt.

I believe my keyboard and keyboard configuration is pretty standard. I load a Norwegian modmap at session start. Everything else with compiz works perfectly, and the shortcuts involving alt work, just with the side effect of throwing my current window away.

Here's the output on xmodmap:
```
shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x6d)
mod1        Alt_L (0x40),  Alt_L (0x7d),  Meta_L (0x9c)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0x73),  Super_R (0x74),  Super_L (0x7f),  Hyper_L (0x80)
mod5        Mode_switch (0x5d),  ISO_Level3_Shift (0x71),  ISO_Level3_Shift (0x7c)
```

And here's the output of xev when I press alt:
```
KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ConfigureNotify event, serial 31, synthetic NO, window 0x3a00001,
    event 0x3a00001, window 0x3a00001, (1281,508), width 178, height 178,
    border_width 2, above 0x1a00548, override NO
```

The last part (ConfigureNotify) comes up after the move is completed.

---

### Post by MeduZa on 2006-11-11
I have the same problem, alt key move the focus application to the next desk on the right, also the water effect stop working :-k 
If I go to the shortcut configuration on System settings all the shortcut to move between desktops are missing :-? 

Alt + left key don't work, also right key.
Alt + Control + left don't work too

any idea?

---

### Post by rallymatte on 2006-11-14
There is another thread for this and there is a solution at the end of it.

[http://ubuntuforums.org/showthread.php?t=287512&highlight=alt+compiz](http://ubuntuforums.org/showthread.php?t=287512&highlight=alt+compiz)

The solution is to go into gconf-editor and find /apps/compiz/plugins/put/allscreens/options/ and disable put_viewport_right_key and put_viewport_left_key to be disabled.

---

