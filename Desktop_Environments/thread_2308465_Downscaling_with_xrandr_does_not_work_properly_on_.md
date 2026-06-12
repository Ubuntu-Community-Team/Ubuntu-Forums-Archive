---
title: "Downscaling with xrandr does not work properly on reboot."
date: 2016-01-03
forum: Desktop Environments
---

### Post by The_Forgotten_King on 2016-01-03
I used the command ```
xrandr --output LVDS1 --panning 1536x900 --scale 1.5x1.5
``` to downscale from 1024x600 to 1536x900. I created a script saying ```
#!/bin/bash
xrandr--output LVDS1 --panning 1536x900 --scale 1.5x1.5
``` to do this every time the system starts. I made it an executable. I then added it to the list of autostart programs, but on reboot, the screen looks like this:
[IMG]http://i.xomf.com/bdzrx.jpg[/IMG]
The desktop is downscaled but does not use the full screen. Upon re-running the command, it works properly. Any ideas on how to fix?

---

