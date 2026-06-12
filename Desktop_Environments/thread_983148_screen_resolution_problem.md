---
title: "screen resolution problem"
date: 2008-11-15
forum: Desktop Environments
---

### Post by roshanjose on 2008-11-15
I installed the XFCE and after upgrading my system, my screen resolutions changed on its own....

I adjusted to 800 X 600...with refresh rate= 60....

Thus the screen fits my monitor... but the browser extends beyond the screen and all icons appear bigger... any idea of wats to be done...

---

### Post by roshanjose on 2008-11-15
and I dont remember my previous settings...must be close to this....

---

### Post by gwoodruff on 2008-11-15
Try a higher res.

---

### Post by roshanjose on 2008-11-16
the highest i have is 832x634..which is also not proper for my resolution....on windows i use 1024x768 which isnt there in my resolution list....

---

### Post by roshanjose on 2008-11-17
my motherboard is Intel D945GCl and monitor is LG..

i tried putting in the highest resolution 832x624, but it doesnt work Maybe 1024x768 might help, but i dont have this in my list.  Someone said that I need to put in the hardware drivers, which i dont know how to obtain.. can anyone help me get this right as it does strain my eyes in viewing....

---

### Post by roshanjose on 2008-11-19
the problem is not yet solved.... Can anyone solve this problem

---

### Post by PhilJ on 2008-11-19
gksu displayconfig-gtk

try using that

Philj

---

### Post by Milkium on 2008-11-19
Try adjusting your monitor's settings by using the buttons on your actual monitor.

---

### Post by linux_tech on 2008-11-19
You can use xvidtune to adjust screen position then edit xorg.conf to get it the way you want it

These links should help with this

adjusting display / screen position using xvidtune
[http://languor.us/adjusting-display-screen-position-using-xvidtune](http://languor.us/adjusting-display-screen-position-using-xvidtune)
[http://howto-pages.org/ModeLines/](http://howto-pages.org/ModeLines/)
[http://www.xfree86.org/current/xvidtune.1.html](http://www.xfree86.org/current/xvidtune.1.html)

DisplayConfigGTK
[https://wiki.edubuntu.org/DisplayConfigGT](https://wiki.edubuntu.org/DisplayConfigGT)

---

### Post by Coreigh on 2008-11-19
Did you use the Xfce Setting Manager / Display applet to adjust your settings? Or did you use another applet or method?

My particular setup is Xubuntu 8.04 on an older Dell (PIII 600 with Intel chipset graphics) and there are *many* setting listed even though most won't work. Have you tried any others? Or does your only show a couple? Have you tried a different refreshrate? Like @75 instead of @60. Have you verified you have the best video driver in use, (vs. a generic one)?

---

### Post by adamgram on 2008-11-22
i'm having the same problem... I think the old moniter I'm using doesn't have a working driver for ubuntu...

---

