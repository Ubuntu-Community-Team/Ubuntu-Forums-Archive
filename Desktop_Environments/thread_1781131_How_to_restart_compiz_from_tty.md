---
title: "How to restart compiz from tty"
date: 2011-06-13
forum: Desktop Environments
---

### Post by ilkerk on 2011-06-13
ubuntu has wake up issues in my computer. However I can login from tty1 as root. Is there a way to restart compiz from tty ? 

When I try "compiz --replace"  from tty1, it gives "Can't open display". I know that I need to allow by "xhost +local:", but I cant since compiz is unusable. 
  
thanks..

---

### Post by garvinrick4 on 2011-06-13
What does this do for you:

```
gconftool-2 --recursive-unset /apps/compiz
```

---

### Post by ilkerk on 2011-06-13
Thanks for the reply. 
I need to give more info. compiz is not broken, I just need to restart it. I usually restart the machine. 
[FONT=monospace]I believe your suggestion resets the setting of the compiz. I only need to restart it, if it is possible from tty.

[/FONT]

---

### Post by garvinrick4 on 2011-06-13
Are you using 11.04 with Unity interface?
```
unity --reset
```
Do you have ccsm installed for settings?
If not look in ubuntu software center and install:

---

### Post by ilkerk on 2011-06-13
Thanks, that also resets the user configuration. 

I\ve just found a solution on the forum. 
I was setting DISPLAY=127.0.0.1:0.0 which requires authorization ( xhost +local:0 ) 
However DISPLAY=:0 doesnt require. I don't know the difference but now I can run X programs such as compiz --replace.

---

