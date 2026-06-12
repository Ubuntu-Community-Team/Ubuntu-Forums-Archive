---
title: "Overlapping Desktops with Dual Monitors"
date: 2009-06-12
forum: General Help
---

### Post by Cable on 2009-06-12
I've sort of got dual monitors working...I can move the mouse and windows between the two monitors and it works great. The problem I'm having is that my second monitor's desktop (in addition to showing on the second monitor) overlaps my main monitor's desktop. See the attached screenshot to see what I'm talking about. Following is the xrandr command I used to get it to look like this...
```
xrandr --auto --output DFP2 --mode 1920x1080 --right-of DFP1

```
Here's some info about my monitors:

Main - DFP2 (right) - 1920x1080
Second - DFP1 (left) - 1280x1024

How can I fix this? Also, how can I save this configuration so that it applies itself when my computer starts? Thanks for any help!

---

