---
title: "Day of Defeat: Source problems"
date: 2007-04-03
forum: Gaming &amp; Leisure
---

### Post by Gorthus on 2007-04-03
This should be my last thread for a while ;) 

Okay, I finally got my video card working and all that (ATI Radeon x800) but now I am having game problems :(

Problems:

1) Sometimes when I try to start the game, I get "The registry is in use by another process, timeout expired"

2) Every time I leave the game, my resolution is changed to 1600x1200

3) When I join a game, local or online, there are a bunch of lines and the HUD and menus flash periodically, making it impossible to play

Questions:

1) Should I set -dxlevel to 70 or 80?

2) Has anyone actually gotten this to run successfully?

3) Should I be running steam through the terminal or just an icon that does:
```
env WINEDEBUG="fixme-all" WINEPREFIX="/home/gorthus/.wine" wine "C:\Program Files\Steam\steam.exe"
```

---

### Post by mrazster on 2007-04-03
I hade some difficulties to get CS-Source to run on my Fiesty 7.04 rigg.

This is how I gotten it to work at atleast playable levels.

First of I run steam with a bash script, that looks like this;
```
#!/bin/bash
WINEDEBUG=fixme-all wine C:/Program\ Files/Steam/Steam.exe -fullscreen \
    -width 1920 -height 1200 -applaunch NN \
    -heapsize 512000 -dxlevel 80
```

But you can of course set wich ever width/height you wish..!

And secondly and probably the thing that had most impact on stability, was to set the Texture shaders and player models at "medium" in the game.


God Luck..!!
Leave Aniso and AA as is in the game and set them from driversettings instead.*(I'm running nvidia...don't if that has anything to do with it thou)*

---

### Post by Gorthus on 2007-04-03
I don't get how you have the code like that... Whats with the tabs and dashes?

In any case, when I go into the advanced video options, and then hit apply, the game closes leaving my resolution at 640x480...

---

### Post by mrazster on 2007-04-04
> **Gorthus said:**
> I don't get how you have the code like that... Whats with the tabs and dashes?

What do you mean..??...just copy and paste the things you want/need from code I posted. Paste it in an empty text document and save. Make it executable with:
```
chmod -x /file/name
```

And just run it....dubbel click on it if you want.

If you are going to use the *-heapsize* switches...then take in count your amount of ram. If you have 1gb or less then something lower than 512000 would be more suitable.

---

### Post by frodon on 2007-04-04
You should read and follow these instructions :
[http://appdb.winehq.org/appview.php?iVersionId=4571](http://appdb.winehq.org/appview.php?iVersionId=4571)

---

