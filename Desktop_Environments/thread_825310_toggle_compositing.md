---
title: "toggle compositing?"
date: 2008-06-10
forum: Desktop Environments
---

### Post by Naegling23 on 2008-06-10
I know that there is a plasmid to toggle compositing in kde4, so I know that it is possible, but I dont know exactly how to do it.

I would like to make a script to turn off the compositing features (like transparency, wobbly windows, shadows, etc) to better performance when Im playing a game.  Something along the lines of the compiz script, 
kwin --replace
launchgame&&
compiz --replace

but for kde's compositing effects.  Does anyone know what I would put here?

---

### Post by steve0921 on 2008-11-08
I would also like to know the answer to this question. Have you made any progress Naegling?

---

### Post by Naegling23 on 2008-11-19
well, I did stumble across the following command:

kwriteconfig --file kwinrc --group Compositing --key Enabled false

I found it in the following thread:
[http://forum.kde.org/showthread.php?tid=6712](http://forum.kde.org/showthread.php?tid=6712)

The only problem is that I cant seem to get it working in a script....maybe you can help me out here.

---

### Post by snova on 2008-11-19
Edit: Ignore.

---

### Post by berot3 on 2009-07-13
i guess thats what u looking for:
```
#!/bin/bash
### gamers-composite-disabler for KDE
# Small script that sets kwin as the window manager
# and then executes YOUR GAME. For use with kwin's compositing

# set to FALSE, doesnt matter it was false or true before
kwriteconfig --file kwinrc --group Compositing --key Enabled --type bool false
kwin --replace & #restart kwin for changes to take effect
sleep 2 #wait 2 seconds before excecute, dont know if its really necesary
/media/games/ut2004/ut2004-64 && 
sleep 2
kwriteconfig --file kwinrc --group Compositing --key Enabled --type bool true
kwin --replace &
```
and thx alot for the link-post :)

---

### Post by Zorael on 2009-07-13
Well, in KDE4 if you just want to toggle compositioning, you can do it with dbus calls.

```
$ qdbus org.kde.kwin /KWin toggleCompositing
```

Neat and fast.

---

