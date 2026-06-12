---
title: "Wine, games, and panels"
date: 2007-07-24
forum: Gaming &amp; Leisure
---

### Post by forrestcupp on 2007-07-24
I have tried running a few games with Wine (Half-Life2, Soldier of Fortune2).  I can get the games to work, but when the games are in full screen, my Gnome panels/task bars are still there covering over the top and bottom part of the game screen.  If the resolution of the game is lower than the resolution of my system, it makes the panels much bigger.  This is pretty annoying, because it covers over where the HUD information is.  I am using the latest wine from their repos.

Does anyone have a solution for this?

---

### Post by jacob01 on 2007-07-24
is the virtual desktop enabled in winecfg if so that could be the problem you could dissable it to get full screen

---

### Post by Energia on 2007-07-24
open the terminal, and write

```
winecfg
```

In Graphic pannel deactivate: Allow the window manager to control the windows

then enjoy in full screen!!! :)

---

### Post by forrestcupp on 2007-07-24
Thanks guys, but that isn't my problem.  I'm not running a virtual desktop and I am allowing the window manager to handle windows.

My problem is not that I can't go fullscreen.  My problem is that I can go fullscreen, but it puts the Gnome panels on it at whatever resolution the game is running at.

---

### Post by Energia on 2007-07-24
> **forrestcupp said:**
> Thanks guys, but that isn't my problem.  I'm not running a virtual desktop and I am allowing the window manager to handle windows.

My problem is not that I can't go fullscreen.  My problem is that I can go fullscreen, but it puts the Gnome panels on it at whatever resolution the game is running at.

if you write:
[B]
winecfg[/B]

and deactivate what i told you in my first answer you could play in wine less panels...(in full screen)

---

### Post by chuckyp on 2007-07-24
Turn desktop effects off before launching the game.  ITs a known bug if you are running beryl or compiz.

---

### Post by Ardrias on 2007-07-24
I solved my problems like this, just because I was running a Virtual desktop for various reasons.

1. sudo apt-get install devilspie
2. Created ~/.devilspie/wine.ds
3. Filled it with the following contents:
```
(if
        (contains (window_name) "Wine desktop")
        (begin
                (above)
                (undecorate)
        )
)
```
4. Save it.
5. Now I set devilspie to start with my session, but that doesnt always work, so whenever I fire up a Wine app I press Alt+F2 to bring up the gnome-launcher and run: devilspie -a

You will need to move the window with the normal alt+drag, for it to cover the panels. Since it hides the panels I tend to start my Wine apps on a different workspace than where I use my IM/Browser/Whatever

Feel free to read up on devilspie, it's quite sweet for a lot more than that.

---

### Post by Energia on 2007-07-24
> **chuckyp said:**
> Turn desktop effects off before launching the game.  ITs a known bug if you are running beryl or compiz.


i use compiz fusion and if I deactivate the flag by winecfg I havent that bug...
So it is only the configuration of wine to be change...

---

### Post by cogadh on 2007-07-24
Adrias, wow that is way too much effort to go to just to get full screen on Wine games.

forrestcupp, just follow what Energia said and turn **off** the "Allow window manager..." option. As long as you allow Gnome to control the app in ful screen, it will keep the panels on the top and bottom of the screen

---

### Post by forrestcupp on 2007-07-24
Sorry Energia.  I misunderstood.  I thought you were telling me to deactivate the virtual desktop and check the "Allow Window Manager to control the windows."

Thank you for that valuable info.

---

### Post by Ardrias on 2007-07-25
> **cogadh said:**
> Adrias, wow that is way too much effort to go to just to get full screen on Wine games.


Well each to their own I guess, also it was what I found to be working best for *me* so I cant comment about other solutions. Also, you dont need to install and make the script each time you know, just run devilspie -a :) Could even put that in a launch-script for the application in question, and there's not even that to think about. Ah well, good luck to the OP!

---

