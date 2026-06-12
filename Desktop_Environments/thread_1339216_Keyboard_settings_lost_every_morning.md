---
title: "Keyboard settings lost every morning"
date: 2009-11-27
forum: Desktop Environments
---

### Post by maedox on 2009-11-27
I just started using Karmic (have been using Ubuntu since around 6.06) and have come across a strange issue.

I usually leave my computer powered on when I leave work so that I can connect to it from home via VPN -> ssh and freenx etc. (My user is always logged in, I just lock the screen whenever I leave.)

When I login the next day it has forgotten all about my keyboard rate settings and my xmodmap changes. (I use xmodmap to make CapsLock type /)
If I log off and on or reboot the settings are correct again.


I have no custom scripts running with cron, and really haven't changed much from the default clean install of 9.10 (x86).

Do any of you have any idea about what could cause this behavior?


I run this script every morning to set my settings back:
```
#!/bin/sh
xmodmap -e "remove Lock = Caps_Lock"
xmodmap -e "keysym Caps_Lock = slash"
gksudo "kbdrate -d 250 -r 30"
```

---

### Post by maedox on 2009-12-01
No one? There has got to be someone that have at least seen this before.

I cannot believe I am the only one with this issue...

Is it just another one in the row of annoying bugs and issues in Karmic?

---

