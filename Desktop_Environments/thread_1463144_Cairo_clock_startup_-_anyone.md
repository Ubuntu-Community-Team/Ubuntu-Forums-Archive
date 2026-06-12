---
title: "Cairo clock startup - anyone?"
date: 2010-04-26
forum: Desktop Environments
---

### Post by Dmoog on 2010-04-26
Have just installed Cairo clock. Lovely little detail on the desktop. But! Really annoying to have to resize it and reposition it every startup. There must be some way round this, surely??

(I have loaded it into the startup list, so it appears automatically, but in the wrong place....)

---

### Post by stinkeye on 2010-04-26
Do you have a .cairo-clockrc hidden file in your home directory.
Any changes you make by right clicking on the clock > properties
should be saved to this file and loaded at startup.
My startup command in startup manager is cairo-clock


my .cairo-clockrc file
```
# This file is machine-generated. Do not edit it manually! I really mean it!!!
x=1390
y=337
width=200
height=200
show-seconds=1
show-date=0
theme=clock-transparant
keep-on-top=0
appear-in-pager=0
appear-in-taskbar=0
sticky=0
twentyfour=0
refreshrate=1
```

Try moving it to where you want, set your preferences and then quit and restart the clock.
If it works out, you should be right at startup.

---

