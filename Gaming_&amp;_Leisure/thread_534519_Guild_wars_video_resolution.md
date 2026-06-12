---
title: "Guild wars video resolution"
date: 2007-08-25
forum: Gaming &amp; Leisure
---

### Post by Ziggyz on 2007-08-25
Ok, so far I can only get Guild Wars to Actually run on CrossOver, and Wine. With cedega, it gives me that unsupported card error at startup.

When ever I try to change the video settings so I can increase the resolution In Game, it freezes up my computer and gets all pixelated, and I have to restart. How can I change these settings without it crashing? Is it possible to change the error I get with cedega to make guild wars run?

Also, I was wondering if there was a platform that could run Guild Wars, with sound (and change the video settings properly)?

---

### Post by Polygon on 2007-08-25
You should just be able to add some command line arguments to the gw.exe file to make it run the way you want

here is what i use (its fully maximized except for the gnome-title bar and my various other menus on the top/bottom of my screen)

```

WINEDEBUG=-all wine "C:\Program Files\Guild Wars\Gw.exe" -dsound -noshaders -windowed

```

If that does not work, stick a -dx8 in there as well, which lowers the quality of the graphics but increases the chances that it will work

and also, try to change your winecfg to emulate a windows 98 enviroment, works well for me.

good luck!

---

### Post by Ziggyz on 2007-08-25
Nice, that worked great. I loaded with that command, and set the resolution. U R gawd, thanks man.

---

