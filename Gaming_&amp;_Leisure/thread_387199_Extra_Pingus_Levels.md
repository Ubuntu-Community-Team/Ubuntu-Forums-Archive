---
title: "Extra Pingus Levels"
date: 2007-03-18
forum: Gaming &amp; Leisure
---

### Post by Eddie Wilson on 2007-03-18
Good Day All,
Is there an easy to play the extra Pingus levels. I've searched and can't find any answer.
Thanks,
Eddie

---

### Post by hikaricore on 2007-03-18
> **Eddie Wilson said:**
> Good Day All,
Is there an easy to play the extra Pingus levels. I've searched and can't find any answer.
Thanks,
Eddie

Sadly there's no easy way that I know of other than command line implemented in the game.

The development of Pingus was dead for awhile, and may still be, so gui selection of extra levels to the best of my knowledge doesn't exist.

However there is always command line:

> [hikaricore@devistate:~]$ pingus --help
Usage: pingus [OPTIONS]... [LEVELFILE]

Options:
   -g, --geometry {width}x{height}
                            Set the resolution for pingus (default: 800x600)
   -h, --help               Displays this help
   --disable-intro          Disable intro
   -w, --window             Start in Window Mode
   -f, --fullscreen         Start in Fullscreen
   -d, --datadir PATH       Set the path to load the data files to `path'
   **-l, --level FILE      Load a custom level from FILE**


So you'd have to run:

```
pingus -l /share/games/pingus/levels/playable/desert4.xml
```

This is only an example, I have build 0.6 of pingus and the levels I have may not be in your version.  Your levels might also reside in a different directory.

Good luck,

--Aaron

---

### Post by Galactic_Overlord on 2009-11-27
Such a pity. Its a beautiful game that deserves more.

---

### Post by diegorodriguezv on 2010-05-23
Since 0.7.2 there is a new way to group levels and to select them from inside the game.

Take a look at: [http://ubuntuforums.org/showthread.php?p=9347205](http://ubuntuforums.org/showthread.php?p=9347205)

---

