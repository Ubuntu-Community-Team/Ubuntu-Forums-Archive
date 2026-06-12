---
title: "xrandr wont change the resolution"
date: 2022-09-03
forum: Desktop Environments
---

### Post by devdlp on 2022-09-03
xrander commands dont actually change the screen resolutions for 
whatever reason. i followed the videos cvt 1920 1080
--addmode and --newmode.
what can i do?
[COLOR=#292929][FONT=Menlo]cvt 1920 1080 60
[/FONT][/COLOR][COLOR=#292929][FONT=Menlo]sudo xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1088 1120 -hsync +vsync
[/FONT][/COLOR][COLOR=#292929][FONT=Menlo]sudo xrandr --addmode [/FONT][/COLOR]XWAYLAND0[COLOR=#292929][FONT=Menlo] [/FONT][/COLOR][COLOR=#292929][FONT=Menlo]"[/FONT][/COLOR][COLOR=#292929][FONT=Menlo]1920x1080_60.00[/FONT][/COLOR][COLOR=#292929][FONT=Menlo]"
gedit ~/.profile
i did all of this and no screen change[/FONT][/COLOR]

---

### Post by TheFu on 2022-09-03
If wayland is being used, xrandr doesn't work.  It is an X/Windows tool, not for Wayland.

---

### Post by devdlp on 2022-09-03
is it possible to not use wayland?

---

### Post by devdlp on 2022-09-03
now im on org but i had a error msg didnt take a screen shot of it but it was for xrandr ill see what i can do

---

### Post by devdlp on 2022-09-03
thank you so much TheFu at the login i changed it ferom wayland and then tried the xrandr tutorial again and bam it worked thanks again

---

### Post by mIk3_08 on 2022-09-04
On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

