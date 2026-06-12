---
title: "Making a second screen NOT show as default?"
date: 2009-12-07
forum: Desktop Environments
---

### Post by gwiener on 2009-12-07
Hello everyone,
I encounter the following annoyance recently:

When I connect a second screen, like an external monitor or a beamer, to my laptop, the resolution switches automatically to a wide desktop that includes both screens (as the connected screen right of the laptop screen).
This is not the behaviour I want. I would prefer that either:
1. The newly-connected screen will **not** start without an explicit setting (like opening "configure display settings") 
2. Both screens will be mirrored (as the option "mirror screens")

I tried to find where to configure this, but I did not find anything.

System spec:
Dell Latitude D630 laptop with an Intel graphic card
Ubuntu 9.10
Standard xorg.conf, listed below
Using compiz

Any ideas how to configure this will be greatly appreciated!
  Guy.

xorg.conf listing:
```
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
        SubSection "Display"
                Depth   24
                Modes   "1440x900" "1280x768" "1024x768"
        EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver "intel"
        Option "AccelMethod" "UXA"
        Option "MigrationHeuristic" "greedy"
EndSection

```

---

