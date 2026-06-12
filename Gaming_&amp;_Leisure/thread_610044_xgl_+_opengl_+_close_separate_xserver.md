---
title: "xgl + opengl + close separate xserver"
date: 2007-11-11
forum: Gaming &amp; Leisure
---

### Post by bash4fun on 2007-11-11
hi everybody

i've got a question
i wrote this script to launch a separate xserver to launch opengl based games or applications

```

#!/bin/sh

X :3 -ac &   # launches a new X session on display 3 
cd /home/robert/.wine/drive_c/Games/CS16
sleep 2   # Forces the system to have a break for 2 seconds 
DISPLAY=:3 wine hl.exe -game cstrike -opengl &  # launches counter strike

```

but it would be nice if the xserver quits automatically on closing the application

by now it stills keeps running showing me some kind of nothing

does anybody know how to help me?

thx

---

