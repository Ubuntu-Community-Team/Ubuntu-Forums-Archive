---
title: "3D programs consume 60% processor"
date: 2008-02-17
forum: Gaming &amp; Leisure
---

### Post by GMWeezel on 2008-02-17
Whenever I run 3D applications, my processor gets bogged down with 50 to 70 percent CPU usage. I have a Geforce 7300GT with the proprietary drivers installed and configured properly (glxinfo posted below for clarification). I have Beryl working correctly and disabling it doesn't reduce CPU consumption of other 3D programs but if I do have a 3D program running, Beryl slows down considerably to about 10 FPS if I'm rotating the cube. Any help appreciated, thank you.

```
$ glxinfo | grep rendering
direct rendering: Yes
```

System Specs:
3.06 GHz P4 HT
GeForce 7300GT
512MBx2 RAM
Running Debian Etch but I had the same issue on Ubuntu

---

### Post by xeth_delta on 2008-02-17
> **GMWeezel said:**
> Whenever I run 3D applications, my processor gets bogged down with 50 to 70 percent CPU usage. I have a Geforce 7300GT with the proprietary drivers installed and configured properly (glxinfo posted below for clarification). I have Beryl working correctly and disabling it doesn't reduce CPU consumption of other 3D programs but if I do have a 3D program running, Beryl slows down considerably to about 10 FPS if I'm rotating the cube. Any help appreciated, thank you.

```
$ glxinfo | grep rendering
direct rendering: Yes
```

System Specs:
3.06 GHz P4 HT
GeForce 7300GT
512MBx2 RAM
Running Debian Etch but I had the same issue on Ubuntu

You may want to run "top" while playing games, in order to find out what is using processing power.

---

### Post by GMWeezel on 2008-02-17
I checked-- it is the game. In this case it's brutal chess but I had the same problem with some SDL 3D games and OpenGL 3D games.

Edit: if it helps, it's mostly Nice usage.

---

### Post by charlieg on 2008-02-17
This is natural.  Games tend to run in threads that repeatedly loop and call the pass off requests to the graphics.  The only way to reduce CPU usage is to throttle frame/physics rates, and that's something few developers will bother to do.  Just playing basic 2D games often makes my fan blow it's little guts out.

---

