---
title: "Ubuntu freezes when ejecting USB devices"
date: 2011-06-20
forum: Desktop Environments
---

### Post by unitshift on 2011-06-20
[FONT=Arial]Hi there,

I'm currently running Ubuntu 11.04 and it has been running fairly smoothly thusfar (despite some unity niggles here and there). I have, however been running into a bit of a problem following an update.

Whenever I eject (safely remove) any usb device from my machine, Ubuntu simply freezes. [/FONT][FONT=Arial]I can't to anything to get it out of this freeze except hard shutdown/restart and [/FONT][FONT=Arial]it happens every single time I safely remove or eject a usb device from the laptop.[/FONT][FONT=Arial] [/FONT][FONT=Arial]When it crashes, my CapsLock indicator light starts blinking and for some reason the laptop starts heating up because the fan starts running higher and higher as if I'm running a very resource hungry application. (I'm pretty sure the heat has caused battery damage as the laptop is less than a year old and after this issue started happening frequently Ubuntu has suddenly started giving me warnings that the battery capacity is down to 40% and that the battery might be damaged, but that's another story).

Any suggestions would be greatly appreciated.



Cheers
[/FONT]

---

### Post by sanderd17 on 2011-06-20
For the battery damage, I always remove my battery when I'm not carrying my computer around. So you might want to do that when testing to prevent further damage.

As a test, could you press CTRL+ALT+F1 when you get it. I hope you see a terminal and can log in. run the command
```

top

```
to see what is causing the trouble. kill it by pressing 'k' and enter the pid

---

