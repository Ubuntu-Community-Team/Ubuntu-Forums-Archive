---
title: "Lenovo 3000 C200 screen brightness issue"
date: 2009-08-03
forum: Desktop Environments
---

### Post by asiwiec on 2009-08-03
I have been using ubuntu 9.04 on my Lenovo for a while and have noticed that shortcuts Fn+F11 and Fn+F10 do not work as they used to when I was using Vesta. What is  the solution?

---

### Post by korenerok on 2009-10-13
I had the same problem as you, and i tried this: type this on the console:

xrandr --output LVDS --set BACKLIGHT_CONTROL native

After that try to use the controls of bright, this work on my C200 (ubuntu jaunty).
But, this change is not permanent, when u reboot, u have to retype...Instead, go to  preferences -> Starting applications. Then u can add a new command, paste that line and its done. Reboot, log in and check the results! good luck

---

