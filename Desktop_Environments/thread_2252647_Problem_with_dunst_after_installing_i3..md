---
title: "Problem with dunst after installing i3."
date: 2014-11-13
forum: Desktop Environments
---

### Post by peto1994 on 2014-11-13
Hi. I installed i3 window manager. When I log into unity, popup notifications look like blue rectangle on top left corner of screen, instead of nice looking default ones. Also notifications when changing volume or brightness are missing. Solutions suggested on the internet recommended to uninstall dunst. However I want just to disable it when I'm not using i3. I tried to find dunst process with ```
ps -A | grep dunst
``` and kill it by it's process id, but it reappeared after ```
notify-send "Text"
```. 
Please help.

---

