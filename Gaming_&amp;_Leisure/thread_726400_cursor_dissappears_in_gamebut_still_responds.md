---
title: "cursor dissappears in game/but still responds"
date: 2008-03-16
forum: Gaming &amp; Leisure
---

### Post by Guinness70 on 2008-03-16
situation
NVidia graphics card working, drivers recently installed via [Envy]("http://albertomilone.com/nvidia_scripts1.html")
amd64 Ubuntu 7.10 Gutsy
running the game Guild Wars via Wine in Windows98 mode, [setup as according the GW site]("http://wiki.guildwars.com/wiki/Guild_Wars_on_Wine")
```
wine "/home/me/.wine/drive_c/Program Files/Guild Wars/Gw.exe" -windowed
```
game and graphics work great.
mouse : Microsoft Intellimouse Explorer setup with [btnx]("http://ubuntuforums.org/showthread.php?t=455656&highlight=btnx") and working AOK.

then all of a sudden the cursor dissappears from the game,
its only the image of the cursor that appears, i can still see its effect on the screen, i can still move it around and it interacts with the game.
another strange thing is that at the same time the number keys (not numpad) 6 7 8 also stop responding.
i cant reproduce it, i cant see a pattern.
i can only say that it happens after a few hours of play.
the only way to get it back is by closing down the game and restarting the game.
when i close the game the cursor does appear on the desktop.

i have been searching hi and low here, most mouse problems reported are on the desktop.
and please bear in mind that im a linux noob.

thank you.

---

### Post by Darganot on 2008-03-16
I have the same problem with the Aquaria demo.  It's why I'm hesitant to buy the game.  It might be an intermittent wine problem.  I try running in different window modes, but the best solution seems to let the window manager control wine and try to set the program or game to fullscreen.  Of course, most games give me a display problem where I can only see half the screen, like Cave Story when I set it to FS.  But Aquaria goes FS just fine.

---

### Post by Guinness70 on 2008-04-12
bump

---

### Post by Cappy on 2008-04-12
I would try ```
killall gnome-screensaver
```
or turning off compiz and seeing if either of those solves the problem.

I actually bought Aquaria because it runs great in Wine =)


You might also want to make sure you have the newest wine
```
wine --version
```
wine-0.9.59

---

### Post by dorath on 2008-04-12
> **Cappy said:**
> You might also want to make sure you have the newest wine
```
wine --version
```

Good call Cappy.  

Guinness70, older versions of WINE have a bug that causes the cursor to disappear.  This has been fixed for some time now, though I don't recall exactly which build contains the fix.  Please open up a terminal and enter the command supplied by Cappy, then let us know which version you're running.

---

### Post by Guinness70 on 2008-04-13
wine-0.9.59
think it update recently also.

disable compiz? ... could try. how? as you can see by my join date, im a linux NOOB.
but ive only recently ventured into compiz, the cursor problem occured before.
is there a part of compiz active even before **ever** going into the compiz menus?

as for the killall screensaver. can i just switch them back on in a menu somewhere?

thanks for the response folks! really! was thinking this was a "local" problem.

---

### Post by Cappy on 2008-04-15
> **Guinness70 said:**
> wine-0.9.59
think it update recently also.

disable compiz? ... could try. how? as you can see by my join date, im a linux NOOB.
but ive only recently ventured into compiz, the cursor problem occured before.
is there a part of compiz active even before **ever** going into the compiz menus?

as for the killall screensaver. can i just switch them back on in a menu somewhere?

thanks for the response folks! really! was thinking this was a "local" problem.

Compiz can be turned off in Gutsy at System-->Preferences-->Desktop Effects
I think Compiz is enabled by default

You can turn the screensaver back on after you finish playing using ```
gnome-screensaver
```

---

