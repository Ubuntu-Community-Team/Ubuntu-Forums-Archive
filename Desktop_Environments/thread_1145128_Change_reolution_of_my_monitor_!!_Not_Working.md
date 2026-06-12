---
title: "Change reolution of my monitor ?!! Not Working"
date: 2009-05-01
forum: Desktop Environments
---

### Post by mr_pro_2020 on 2009-05-01
i can't change my resolution 

when i open Display 

i have only one resolution to choose

1280 X 800 

?!!

---

### Post by KhurramM on 2009-05-01
use:

xrandr -q

to determine the available modes:

next:

xrandr -s 1280 X 800  -r 60 (just an example, yours may vary)

man xrandr for details

I hope this helps.

---

### Post by mr_pro_2020 on 2009-05-02
No result 

and when i tried 

> 
yahia@yahia-laptop:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1400
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       59.9*+
TV disconnected (normal left inverted right x axis y axis)
yahia@yahia-laptop:~$ 


and Also 
> 

yahia@yahia-laptop:~$ xrandr -s 1280X800 -r 60
Size index 1280 is too large, there are only 1 sizes
yahia@yahia-laptop:~$ xrandr -s 1024X760 -r 60
Size index 1024 is too large, there are only 1 sizes
yahia@yahia-laptop:~$ xrandr -s 1280X800 -r 60
Size index 1280 is too large, there are only 1 sizes


---

