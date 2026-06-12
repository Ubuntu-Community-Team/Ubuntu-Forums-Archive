---
title: "Noob Help required"
date: 2008-02-24
forum: Desktop Effects &amp; Customization
---

### Post by BRFC on 2008-02-24
Could anybody possibly give me some sort of walk through for the different effects/settings  used on this video as I've just spend all day installing 7.10 and and now I want it to look as good as it runs. I have Compiz Config installed but admit that I'm a bit useless at making it look like I want.

[http://www.youtube.com/watch?v=E4Fbk52Mk1w](http://www.youtube.com/watch?v=E4Fbk52Mk1w)

---

### Post by fracturedmorals on 2008-02-24
Compiz is easy enough to tweak.

What effects do you specifically want and what sort of video card do you have?

--Ian

---

### Post by wesley_of_course on 2008-02-24
Greetings !  Here's a nice thread here ; [http://ubuntuforums.org/showthread.php?t=659282](http://ubuntuforums.org/showthread.php?t=659282)
        and here ;[http://forum.compiz-fusion.org/showthread.php?t=5303](http://forum.compiz-fusion.org/showthread.php?t=5303)

          This is a good start , it'll take some read'in but for eye-candy , (if this is what your after ) , this should get you going ! And post back so we'll here how it went . Have fun .        :)

---

### Post by BRFC on 2008-02-25
Thanks for the help.
System Details
AMD Sempron 2800 running at 1600 
1Gb Ram
Graphics card is Nvidia Geforce 7600GS 512mb
40Gb HD, 80Gb HD & 250Gb Network HD

Everything seems to be running sweet just want it to look as good now, so time to start tinkering.  I really like the Expo setup at the beginning, with the ring switcher plugin.

---

### Post by fracturedmorals on 2008-02-26
Alright....here's what I generally do for compiz happiness:

**Performance tweaks:**

Display:
```
open up ccsm
go to general>display
uncheck "Auto-detect refresh rate" and set refresh rate to 200.
```
Note:
If you aren't going to use wobbly windows, the "Sync To Vblank" option reduces tearing

Nasty flickering fade:
```
Uncheck "Fading Windows"...
The animation plugin handles this just fine
```

Expo:
```
For expo, check expo, and then check "Mipmaps" (This smooths out the zoomed-out desktop),
Click on the "Actions" tab and set the shortcut of your preference (Mine is personally the upper left corner+right click)

```

For decent wobbliness:
```
Check wobbly windows, and uncheck "Snap Inverted" (Otherwise they WILL go crazy in expo)
```

Drop shadows can be configured in "Window Decorations"

If you turn on "Scale addons", then the OSX-like "Scale plugin will allow you to preview windows with a right click, and close them with a middle click.

If you check "Ring Switcher", Super(Windows)+Tab will act like Alt+Tab except with the ring (Although Shift switcher gives you a nice cover-flow-esque replacement with the same shortcut)

If you have anything else to ask about, don't hesitate. I have no life.

---

### Post by BRFC on 2008-02-27
Cheers for that, I'm stuck in the office at the moment but will give these a try when I get home.  Just got ta say again how much I'm enjoyong the whole Linux experience.:)

---

