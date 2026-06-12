---
title: "Auto Run Script at GDM Start"
date: 2011-04-30
forum: Desktop Environments
---

### Post by Dogsworth on 2011-04-30
Greetings,

I'm on Natty, but this was a problem for me on Maverick as well. Since my mouse is *way* too fast in Ubuntu even on the slowest settings (a topic for another discussion), I run a shell script at startup to fix this. Of course, the script is only run when I log into my account.

Is there a way to have this script run at system start so that it affects all users? I already tried copying my fixmouse.sh script to /usr/share/gdm/autostart/ to no avail.

Thanks in advance,

Dogsworth

PS:
If it's germane to the discussion, here are the contents of fixmouse.h:

```
#!/bin/sh

xinput --set-prop 10 "Device Accel Constant Deceleration" 2
xinput --set-prop 10 "Device Accel Velocity Scaling" 1
```

---

### Post by Krytarik on 2011-05-01
Try adding them to GDM's startup script by following this guide (meant for xrandr):
[https://wiki.ubuntu.com/X/Config/Resolution#Setting%20xrandr%20commands%20in%20kdm/gdm%20startup%20scripts](https://wiki.ubuntu.com/X/Config/Resolution#Setting%20xrandr%20commands%20in%20kdm/gdm%20startup%20scripts)

But it may be that 'gnome-settings-daemon' overrides these settings upon login.

Greetings.

---

### Post by tock on 2011-10-13
You might also try adding a pause to the script.  It worked for me with gnome.  Without the pause the mouse speed would not change.

---

