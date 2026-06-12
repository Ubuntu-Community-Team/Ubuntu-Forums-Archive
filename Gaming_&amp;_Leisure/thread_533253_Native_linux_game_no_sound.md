---
title: "Native linux game no sound"
date: 2007-08-23
forum: Gaming &amp; Leisure
---

### Post by Ziggyz on 2007-08-23
I installed quake 3 and enemy territory, and I get no sound. What's wrong?

---

### Post by ubuntu.daemon on 2007-08-23
are you running any other applications that use sound at the time??  Do you have a sound card or are you using the mobo?

---

### Post by Ziggyz on 2007-08-24
I am using the mobo, and I dont have any other sound emmiting applications.

---

### Post by Dark Aspect on 2007-08-24
> **Ziggyz said:**
> I installed quake 3 and enemy territory, and I get no sound. What's wrong?
I have found this [HOWTO]("http://ubuntuforums.org/showthread.php?t=42492") very useful for getting native games too work with sound,I have actually created a  script file for Return to the castle wolfenstein that works with sound that reads:

#!/bin/bash
# Needed to make symlinks/shortcuts work.
# the binaries must run with correct working directory
  cd "/home/administrator/wolfenstein"
  kbuildsycoca
  artsd -F 6 -S 256
  artsdsp -m ./wolfsp.x86 $*
  exit $? 
  
If you have installed arts and libkonq4 though the Synaptic package manager it will work.Let me know if it works or if it didn't,if you need anymore help feel free to PM me,I have a good idea on how to fix this if this does not work.

I think enemy territory has additionally steps for its sound to work

---

### Post by ubuntu.daemon on 2007-08-24
well that and just make sure you arent running any other apps, and maybe you are just having bad luck bc a system notification pops up.  Like i used to have issues with starcraft, until i installed another sound driver for that game to draw from....  like i used arts for games/music and oss for my system notifications i think

---

### Post by Ziggyz on 2007-08-24
Ok thanks for the help, ill check it out.

---

