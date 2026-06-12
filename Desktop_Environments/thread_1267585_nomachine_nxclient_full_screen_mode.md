---
title: "nomachine nxclient full screen mode"
date: 2009-09-15
forum: Desktop Environments
---

### Post by misha680 on 2009-09-15
Hi all:

This is driving me nuts as its simple and seems simple to do but I am having the hardest time...

I use nxclient to connect to a session in Fullscreen mode or "Available Area". Either way it starts out Fullscreen the _first_ time, but when I connect to it from work at a different resolution, and then come back home, it does not connect fullscreen anymore.

This adds a little more complication too as I am connecting in a window manager-less environment at home, and thus have to use xrandr to reset the resolution of the child.

Any help much appreciated.

Thank you
Misha

Here is my hackey solution. My /usr/bin/nxclient-run script:

```

#!/bin/sh
nvidia-settings -l
syndaemon -d -t
NX_DISPLAY=`ps -efw | grep nxagent | sed s/.*:// | head -n 1`
DISPLAY=:$NX_DISPLAY xrandr -s 5
/usr/NX/bin/nxclient --session /home/misha/.nx/config/local.nxs &
exec xterm

```
[/code]

---

