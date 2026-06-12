---
title: "Font &amp; Brightness"
date: 2007-09-20
forum: Desktop Effects &amp; Customization
---

### Post by Ascension on 2007-09-20
I need some help making my font not look so choppy and my screen not being so bright, Ive went into my main monitor settings and changed it all but my monitor is still really really bright? Any suggestions?

---

### Post by hyperair on 2007-09-20
Install the package called "xgamma". Then use it in the terminal like this:
```

xgamma -gamma <value>

```

The gamma value is anywhere between 0.000 to 1.000, 1.000 being the brightest. Then when you've selected one that you're happy with, tweak your xorg.conf file (in your Monitor section):

```

Gamma <value>

```

For example, mine looks like this:
```
Section "Monitor"
    Identifier     "LCD52V"
    HorizSync       31.0 - 61.0
    VertRefresh     56.0 - 75.0
    Gamma           0.65
    Option         "DPMS"
EndSection

```

---

### Post by Ascension on 2007-09-20
That worked great for the brightness, any suggestions for the font? Like so its no so pixelized.

Where do I find? my xorg.conf file?

---

### Post by hyperair on 2007-09-20
Your xorg.conf file is /etc/X11/xorg.conf. For the fonts...

For your fonts, here's a guide: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_smooth_fonts](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_smooth_fonts)

---

