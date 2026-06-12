---
title: "Stop gnome-panel automatic respawn"
date: 2007-01-09
forum: Desktop Environments
---

### Post by studentism on 2007-01-09
Hi All,

I was wondering if there's a way to stop the respawn on a ```
killall gnome-panel
``` or even a kill by pid.  It's a long story I'd rather not get into, but I'm trying to fix a fullscreen issue with three screens (two by TwinView and all three linked with Xinerama).  I've recompiled metacity to be xinerama unaware, so some applications do full screen across all three monitors, but other ones only full screen up to the panels (I'm referring to top layer fullscreen here, where the application eclipses the panels).

I fixed a similar problem in XFCE by running a script to kill the panels, run the application, and then recreate the panels, but I'm now being forced to use the GNOME desktop.

Is there any way to accomplish this without a great deal of hassle?  Thanks in advance.

---

### Post by studentism on 2007-01-09
Found a somewhat working solution.

```
#!/bin/bash

gnome-session-remove gnome-panel
[program]
gnome-panel&
```

With some programs, the panel will respawn immediately after it opens (even with a ```
wait
``` after the program invocation), but thankfully gmplayer (which is what I need working) does not.

If anybody has any other solutions, I'm all ears, but this solves my particular issue.

---

### Post by Ryan Marcus on 2007-02-06
If you don't want to have to keep the terminal window open to hold onto your gnome panels, you can:

```

gnome-session-remove gnome-panels
[program]
screen gnome-panels

```

---

### Post by mcduck on 2007-02-07
You can go to System/Preferences/Session and under the 'Current Session'-tab find Gnome-panel and change it's style from Restart to Normal. Now it shouldn't autospawn any more if you kill it :)

---

