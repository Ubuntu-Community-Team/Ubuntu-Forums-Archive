---
title: "Screen Rez issues"
date: 2006-10-15
forum: Gaming &amp; Leisure
---

### Post by PendragonUK on 2006-10-15
I have a problem with my LCD monitor, it really doesn't like it when a program attempts to output a rez and refresh rate it doesn't understand.

I have learnt to edit stuff when installing the nVidia drivers. So the normal desktop looks fine. Running at 1280x1024 & 75Mhz refresh rate using the Horizontal and Vertical settings for my LCD monitor. I looks like games just skip this info and go their own way...

```

Section "Monitor"
    Identifier    "LCD 1280x1024"
    Option        "DPMS"
    HorizSync    31-81
    VertRefresh    56-75
EndSection

```

```

Section "Screen"
    Identifier    "Default Screen"
    Device        "nVidia 7900GT"
    Monitor        "LCD 1280x1024"
    DefaultDepth    24

```

```

SubSection "Display"
        Depth        24
        Modes        "1280x1024_75" "1024x768" "800x600" "640x480"
    EndSubSection

```


So is there a way of forcing all programs that run in full screen mode to use the same monitor setup, rez and refresh rate that is set in the xorg.conf Or do I have to edit each one individually?

If it's done individually anyone know the file I have to edit for Enemy Territory? Then I will have to go through each game I have install that grabs full screen, Grrrrr...

---

### Post by PendragonUK on 2006-10-17
Bump...

---

### Post by klerfayt on 2006-10-17
your question is a little confusing; are you saying that if game uses 800x600 in fullscreen mode then you get wrong/unwanted screen refresh rate?
one way to fix this is to add "Modeline" for every resolution in your xorg.conf file;
open console and use command "gtf" to calculate it for you - e.g:
"gtf 800 600 75" gives you:
# 800x600 @ 75.00 Hz (GTF) hsync: 47.02 kHz; pclk: 48.91 MHz
  Modeline "800x600_75.00"  48.91  800 840 920 1040  600 601 604 627  -HSync +Vsync
Add the modeline part (without _75.00) in your xorg.conf under Section "Monitor" 
Modeline "800x600"  48.91  800 840 920 1040  600 601 604 627  -HSync +Vsync

-I'm not sure what "-HSync +Vsync" does though...

---

### Post by PendragonUK on 2006-10-19
I will give it a go... I'll report back with my results so if there is anyone else with the problem they can use the fix...

---

### Post by PendragonUK on 2006-10-19
OK that works... well including the correct refresh rate for each rez at each colour depth.

---

