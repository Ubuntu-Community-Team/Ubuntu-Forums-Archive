---
title: "[SOLVED] Games not running"
date: 2008-12-19
forum: Gaming &amp; Leisure
---

### Post by floborg on 2008-12-19
I've installed Nexuiz and Lincity-NG in Hardy 32 using Synaptic, but neither runs.  When started from the Applications shortcut, my screen flickers and the mouse jumps to the upper left-hand corner of the screen.  No new windows are opened and nothing is listed in the process monitor.  This happens when using Compiz or Metacity.

When run from the terminal, I get this:

```
Starting lincity-ng (version 1.1.2)...
[/home/erik/.lincity] is in the search path.
[/usr/share/games/lincity-ng] is in the search path.
LINCITY_HOME: /usr/share/games/lincity-ng
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  134 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x66
  Serial number of failed request:  123
  Current serial number in output stream:  125
```

Now, I don't have a dedicated GFX card, but I can run Compiz just fine off my Intel onboard GFX.  I wouldn't think that would matter for Lincity.

---

### Post by floborg on 2008-12-19
Ok, so I got a little further by trying to change the resolutions.  I run my desktop in 800x600 (smallish CRT monitor).  LinCity can be made usable with command line options.  I could get it to run full screen in 800x600.  Nexuiz won't play ball.  It only runs in windowed mode and in a resolution that wasn't the 800x600 I wanted.  Most of the window is cut off.  There's also no obvious way to select another window or quit Nexuiz, so I have to use CTRL-ALT-BACKSP.

---

### Post by Perfect Storm on 2008-12-20
Nexuiz
```
nano ~/.nexuiz/data/config.cfg
```

add

vid_height "600"
vid_width "800"

save [ctrl]+[o] and exit [ctrl]+[x]

[img]http://www.imageviper.com/displayimage/131519/0/nexnano.png[/img]

---

### Post by floborg on 2008-12-20
Worked.  Thanks.

---

