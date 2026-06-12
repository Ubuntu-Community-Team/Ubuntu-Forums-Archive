---
title: "Tips for Getting Out of a KDE Crash"
date: 2010-04-12
forum: Desktop Environments
---

### Post by r4e on 2010-04-12
Every so often with KDE4 I get into a situation where something goes wrong within the desktop environment, causing the machine to become nearly unresponsive with the dual core CPUs going to 100% and the screen going into an artifact meltdown. I can usually mostly recover from this by dropping to a different TTY (CTRL+ALT+F2), logging in and executing:

```

killall kwin
export DISPLAY=:0
kwin &

```

Which restarts the Window manager. That improves the desktop environment situation. Then I switch back to the KDE environment (usually either CTRL+ALT+F7 or CTRL+ALT+F8 ). I launch krunner (ALT+F2) and execute:

```

kquitapp plasma && plasma &

```

Which again seems to help restore the desktop to pre-crash state.

Usually there are still artifacts in the taskbar though. Does anyone know how to reset the taskbar without a reboot? Not having to reboot after a serious crash is what makes linux so awesome. 

Thanks!

r4e

---

### Post by Untitled_No4 on 2010-04-12
Alt+F2 then
```
kquitapp plasma-desktop
```

Alt+F2 again and
```
plasma-desktop
```

Edit:
By the way, you might want to try and look where the problem is in the first place. I have KDE4.4 running for days without any such problems.

---

### Post by r4e on 2010-04-12
That did the trick. Thanks!

Yeah, I'll probably try to hunt down the problem when I have more time available. KDE 4.4.2 is stable enough that it's pretty rare for this to happen. I have a hunch that it has something to do with running out of memory due to running VirtualBox.

---

