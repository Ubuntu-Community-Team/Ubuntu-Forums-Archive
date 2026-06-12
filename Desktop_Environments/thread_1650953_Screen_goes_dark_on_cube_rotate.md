---
title: "Screen goes dark on cube rotate"
date: 2010-12-22
forum: Desktop Environments
---

### Post by lukech95 on 2010-12-22
Just installed 11.04 (Natty).  Graphics card is Radeon 9200

When I enable Cube in the compizconfig settings manager and rotate the cube, the cube goes almost black.  This happens with both drag and keyboard rotate. The background is fine.  Everything is defaults and no other effects are enabled.

Also, the entire screen goes dark when "opacity when not rotating" is set to anything but 100%.

This worked fine with with my previous version 8.04, though I think it used a proprietary driver.

Questions:

Should I be using a proprietary driver this card?  Apparently you have to install a long list of packages first: [FONT=Verdana, Verdana, Helvetica, sans-serif][SIZE=1]XFree86-Mesa-libGL[/SIZE][/FONT][FONT=Verdana, Verdana, Helvetica, sans-serif][SIZE=1]           libstdc++[/SIZE][/FONT][FONT=Verdana, Verdana, Helvetica, sans-serif][SIZE=1]           libgcc[/SIZE][/FONT][FONT=Verdana, Verdana, Helvetica, sans-serif][SIZE=1]           XFree86-libs[/SIZE][/FONT][FONT=Verdana, Verdana, Helvetica, sans-serif][SIZE=1]           fontconfig[/SIZE][/FONT][FONT=Verdana, Verdana, Helvetica, sans-serif][SIZE=1]            expat[/SIZE][/FONT][FONT=Verdana, Verdana, Helvetica, sans-serif][SIZE=1]            freetype[/SIZE][/FONT][FONT=Verdana, Verdana, Helvetica, sans-serif][SIZE=1]           zlib[/SIZE][/FONT]

Any ideas for how to diagnose or fix this?

Thanks!

---

### Post by karthick87 on 2010-12-22
Welcome to ubuntuforums :)

Try,
```
compiz --replace
```

---

