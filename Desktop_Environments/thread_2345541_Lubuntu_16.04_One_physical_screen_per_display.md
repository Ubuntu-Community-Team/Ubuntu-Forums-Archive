---
title: "Lubuntu 16.04: One physical screen per display?"
date: 2016-12-05
forum: Desktop Environments
---

### Post by emag37 on 2016-12-05
Hello,

I am using Lubuntu 16.04 and am trying to set up two screens as follows:

Display 1 (VGA output): Main display with keyboard and mouse
Display 2 (DVI output): Display with no input, just to display media

I understand that they've done away with static Xorg.conf files and everything is configured automatically, so I've been using XRandR commands to set the displays up appropriately on boot-up. Everything works well, except it treats the two screens as one giant display (echo $DISPLAY is always 0.0). So if I want to display an application on only one display or the other, I have to pass the appropriate --geometry flag to the application. Is there a way to force the X server to identify the screens as two seperate displays, such that I have $DISPLAY=0.0,0.1 or just 0,1? That way I could just set the application as fullscreen and not have to screw around with window geometry. 

I believe it uses an Intel graphics chip.

Thanks!

---

