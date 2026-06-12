---
title: "Keyboard shortcuts to unity launcher"
date: 2013-01-14
forum: Desktop Environments
---

### Post by Hiutale on 2013-01-14
Hey,

I'm new user at ubuntu community and wondered following:

Is it possible to make keyboard shortcuts (like a shortcut for windows-key) for unity launcher?

The idea is to download cairo dock and put a shortcut to the Windows-key to open the dash.

br
Markus Salla

---

### Post by stinkeye on 2013-01-14
Make a script to initiate the windows key using xdotool.

Install xdotool...
```
sudo apt-get install xdotool
```

xdotool script...
```
#!/bin/bash
xdotool key Super
```

Not familiar with cairo-dock. You may be able to just create a launcher on the dock
that uses the **xdotool key Super** command or points to the bash script.

---

### Post by grahammechanical on 2013-01-14
Have you tried holding down the Super (Windows) key? Have you tried giving the super key a tap?

You may find that you already have keyboard short cuts.

Super+A = Open applications lens
Super+F = Open file lens
Super+V = Open video lens
Super+M = Open music lens

And there is more. At least with 12.10

Regards.

---

