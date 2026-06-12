---
title: "[SOLVED] Constantly moving up and left"
date: 2008-09-06
forum: Gaming &amp; Leisure
---

### Post by benbelly on 2008-09-06
When I start certain games (Egoboo in Linux, Psychonauts and CrimsonLand in Wine) the cursor or my character move continually to the top left corner of the screen.  The only devices I have plugged in to my PC are the monitor, speakers, my Microsoft Ergonomic Keyboard and Microsoft Sidewinder mouse.  Could my system be rejecting my MS devices?  ;)  Seriously, can someone advise me on how to discover what is causing this behavior?

Thanks,
-Ben

---

### Post by BenAshton24 on 2008-09-06
Hey! Make sure that you have disabled all effects (some games don't like compiz) system --> preferences --> Appearence click on the "visual Effects" tab and select "none"

Hope This Helps :D Ben. (same names :P)

btw, for future reference any wine related topics should be posted in the wine section (i'm sure this one will get moved at some point :P)

---

### Post by benbelly on 2008-09-06
> **BenAshton24 said:**
> Hey! Make sure that you have disabled all effects (some games don't like compiz) 
  I think I've isolated the problem to my sidewinder gaming mouse.  I unplugged it and tried a different mouse and the problem went away. Of course, I didn't think of trying that until I typed up what devices I'm using.  <blush>
> **BenAshton24 said:**
> 
btw, for future reference any wine related topics should be posted in the wine section (i'm sure this one will get moved at some point :P)

  I don't think this is a wine problem because it happens with that Egoboo game.  I'll try disabling compiz to see if the problem goes away - maybe some interaction between the mouse and the display software?  One hopes not, but crazier things happen.

-Ben

---

### Post by benbelly on 2008-09-06
The problem persists even with all visual effects disabled.  I guess there's some sort of bug with the Sidewinder gaming mouse and some applications.  I bet there's a common library . . . Time to start searching.

  Is there a tool to find common dependencies between packages?

---

### Post by benbelly on 2008-09-07
I found out that I needed to change my xorg.conf to deal with my mouse.  Go figure.  :)

  I ended finding what I needed at** [Re: [SOLVED] Sidewinder Gaming Mouse Configuration Help]("http://ubuntuforums.org/showthread.php?t=613697")**.  This is the configuration I used:

```
Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
	Option	    "CorePointer"
        Option      "Protocol" "ExplorerPS/2"
        Option      "Device" "/dev/input/mice"
        Option      "Buttons" "5"
        Option      "ZAxisMapping" "4 5"
        Option      "ButtonMapping" "1 2 3 6 7"
        Option      "Emulate3Buttons" "no"
EndSection
```

---

### Post by Vadi on 2008-09-07
I'm experiencing this issue in all Quake-based games also, but in none others.

---

