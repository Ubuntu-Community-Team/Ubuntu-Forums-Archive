---
title: "[SOLVED] Hlep! Installed Compiz Fusion, now terminal is white"
date: 2007-07-05
forum: Desktop Effects &amp; Customization
---

### Post by NewJack on 2007-07-05
Like the title says.  I installed Compiz Fusion with what seemed to be no problems.  Effects were fine and everything.  For some reason though, when I go to open the terminal it appears to be solid white in color and I can't see any text at all.  Any suggestions would be most welcome.

Thanks!
Joe

P.S.-  I was also missing the windows buttons (Min, Max, Close).  I installed Emerald and that seems to have done nothing also.  Thanks again.

---

### Post by isaacj87 on 2007-07-05
Can you post a pic?

---

### Post by Jem00 on 2007-07-05
Maybe it just changed ur profile settings in the terminal....

---

### Post by NewJack on 2007-07-05
Sorry, I am not home right now to grab a pic.  Just imagine you have opened your terminal and instead of seeing any text or even a border, it is just white.

---

### Post by NeoLithium on 2007-07-05
I had the same problem.  In your xorg.conf, edit your screen section to add this line:
```

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV34 [GeForce FX 5200]"
        Monitor         "E90f-2"
        DefaultDepth    24
[COLOR="Red"]**        Option          "AddARGBGLXVisuals" "True"**[/COLOR]
        SubSection "Display"

```

---

### Post by NewJack on 2007-07-06
Neo, I'll give that a try when I get home.  Thanks!

---

### Post by NewJack on 2007-07-06
Here is a screenshot:

[[IMG]http://img458.imageshack.us/img458/2540/screenshotmk4.th.png[/IMG]](http://img458.imageshack.us/my.php?image=screenshotmk4.png)

Since I can't type in the Terminal, how should I go about entering that line into the /etc/X11/xorg.conf?


Another problem I have noticed is that I can only move windows around by pressing ALT+left mouse.

Thanks

---

### Post by NewJack on 2007-07-07
Bump

---

### Post by kraymore on 2007-07-07
if you disable the desktop-effects button you should have visibility in terminal.  then its a simple copy and paste.  

and i just tried it out and that line does allow me to enable desktop-effects and not see white in terminal and i still get window borders, etc.   wonderful

---

### Post by BoneSaw on 2007-07-07
if you dont want to turn off desktop effects you can hit alt+f2 to run a command

---

### Post by NewJack on 2007-07-07
Well, I just started my box and all of the sudden the terminal works fine.  I don't know exactly what did the trick cause I tried so many different options to get this to work.  

The last thing I tried was adding the blue highlighted lines to the "Device" Section in my xorg.conf (as mentioned by Starcraft.man in another thread- Thanks apparently go to him).

Section "Device"
        Identifier      "Generic Video Card]"
        Driver          "nvidia"
        [COLOR="RoyalBlue"]BusID           "PCI:1:0:0"
        Option          "AddARGBGLXVisuals"         "True"[/COLOR]
EndSection

But last night, even after adding those lines and restarting I was still having the "White Terminal" problem.  Wonder why it is working all of the sudden?  At least it is working

Thanks guys!!!

---

