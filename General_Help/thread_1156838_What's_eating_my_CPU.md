---
title: "What's eating my CPU?"
date: 2009-05-12
forum: General Help
---

### Post by GuiGuy on 2009-05-12
This is more an observation than a cry for help, but:

PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
5086 auser    20   0  865m 225m  32m R  100 11.5   5:48.60 firefox

Either its firefox or ubuntu 9.04 or both, but it's starting to drive me crazy. And it's not just firefox. There are other applications that periodically pop up to consume all that's available, thereby bringing the system to a halt. 

AMD AM2 X2 
4G RAM
SATA (hah!!) drives

---

### Post by mb_webguy on 2009-05-12
Programs may sometimes briefly use 100%.  This is normal, but should only last for a second or two.  If Firefox is using 100% CPU for an extended period of time, then there is indeed a problem somewhere, and my guess would be Flash.  Try starting Firefox from the terminal to see any error messages that might be suppressed by the GUI.

As for other programs, without knowing the specific programs, it's hard to say.

---

### Post by GuiGuy on 2009-05-12
> **mb_webguy said:**
> Programs may sometimes briefly use 100%.  

This is not briefly. This is prolonged, like anything from a few seconds to minutes. Couple with the [poor SATA performance]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119730") under Ubuntu I'm thinking my options are becoming clearer.

---

