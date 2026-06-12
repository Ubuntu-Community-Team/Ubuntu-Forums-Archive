---
title: "Finity Flight"
date: 2008-08-06
forum: Gaming &amp; Leisure
---

### Post by curvedinfinity on 2008-08-06
Hey everyone, me and my two friends have just released a new open source game called Finity Flight. It runs on our new cross-platform game client called MirthKit. Yeah, I'm the same guy who released the four "Finity Flight" games from a couple years ago. This is what I've been working on in my spare time for the last two years, so I hope you all like it.

Download the .deb here:
[http://www.mirthkit.com/?page_id=5](http://www.mirthkit.com/?page_id=5)

The .deb up there is an arcade which you can play the game through (currently only Finity Flight is available). After you play the game, you'll have automatically downloaded all of the game's source, so if you want to look at it, here are instructions for viewing the source:
[http://devs.mirthkit.com/index.php?title=Modifying_Existing_Games](http://devs.mirthkit.com/index.php?title=Modifying_Existing_Games)

If you can't get it to run, I'd appreciate it if you respond back with the symptoms. :)

Pics for clicks:
[IMG]http://www.mirthkit.com/wp-content/themes/CIG/images/ss4.png[/IMG]

Thanks to everyone who tries it out!

If you're interested in making a game for MirthKit, there's tons of information published on that wiki. Just give me a holler. We're being quiet for now, since we want to make sure it runs well on a wide variety of hardware, but soon enough we'll start being more vocal, and make appearances on various news websites. We aim to basically be the open source equivalent to the arcades on the 360, PS3, and Wii, so I hope you can appreciate the effort. ;)

---

### Post by Sandlst on 2008-08-07
This game rocks!  I usually don't go for arcade shooters, mostly because the "cool guns" usually take forever to unlock, or only have limited ammo that makes me want to save them up and never use them, but this game circumvents those problems quite nicely.  Giving weapons special attacks is a really nice touch too, and the games pace fits me just right. I would definitely be willing to buy some add-on content for this game.  I ran the MirthKit client from a terminal, and noticed these error messages after exiting the client, although I didn't notice any adverse effects while playing:
```
libpng error: invalid distance too far back
libpng error: IDAT: CRC error
libpng error: IDAT: CRC error

```

Followed by many lines of ```
libpng error: invalid distance too far back

```
Great job on this game, I'm going to be sure to keep my eye on Curved Infinity Games!:guitar:

---

### Post by curvedinfinity on 2008-08-07
Thanks for the bug report and especially the warm review!

I can promise you'll have an expansion to buy soon. We're in the process of adding bosses! :)

---

### Post by kidux on 2008-08-07
Sweet game! Takes a little bit to play downloading files over my satellite internet connection, but it's beautiful and well done nonetheless. No errors spit out by console. The only change I can request is keyboard directional be added, but otherwise great job!

---

### Post by curvedinfinity on 2008-08-07
Thanks kidux! I'm adding keyboard directional to our task tracker. ;)

---

### Post by wingnux on 2008-08-07
wingnux@wingnux-desktop ~ $ mirthkit 
Floating point exception

I'm running Ubuntu Hardy 32bit, the launcher started ok, then I selected the game and it started loading, the loading screen crashed with no error messages and then it didn't show up again. After running the launcher from the console I got the above message.
Compiz was running when it first crashed.

---

### Post by curvedinfinity on 2008-08-07
Hmmm... that's a really odd one. Would you mind if I sent you a new .deb with some extra debug stuff?

---

### Post by wingnux on 2008-08-07
Not at all, fell free to!

---

### Post by curvedinfinity on 2008-08-07
Heya wingnux, please download/install [http://storage.mirthkit.com/mirthkit_1.1-2.deb](http://storage.mirthkit.com/mirthkit_1.1-2.deb) and run it with the -debug argument. So that's...

mirthkit -debug

from any directory

And thanks for helping us out!

---

### Post by Grone1985 on 2008-08-08
@ curvedinfinity

I'm running a 64 bit Ubuntu version... How do I install the game on it?
Thanks!

---

### Post by curvedinfinity on 2008-08-08
Heya Grone1985,
Try these instructions:
[http://www.unixtutorial.org/2008/03/install-32-bit-deb-packages-on-64-bit/](http://www.unixtutorial.org/2008/03/install-32-bit-deb-packages-on-64-bit/)

If that doesn't work, they were the top link on this search, so see if there is anything else that's useful in it...
[http://www.google.com/search?q=Ubuntu+installing+32bit+deb+on+64bit&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=Ubuntu+installing+32bit+deb+on+64bit&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

Hope that helps! :)

---

### Post by wingnux on 2008-08-08
Here is the output:

> wingnux@wingnux-desktop ~ $ mirthkit -debug
Initializing client...
Retrieved window size preference: 800x600
Initialized Squirrel
Initialized curl
Initializing MirthKit subsystems...
Initializing amaryllis subsystem
Initializing albillo subsystem
Initializing andromeda subsystem
Initializing MirthKit subsystems complete
Initialization complete
Registering Squirrel bindings...
Registering binding: update
Registering binding: screen
Registering binding: flush
Registering binding: srand
Registering binding: version
Registering binding: loadNut
Registering binding: doNut
Registering binding: http
Registering binding: progress
Registering binding: open
Registering binding: close
Registering binding: send
Registering binding: receive
Registering binding: background
Registering binding: modifyWindow
Registering binding: revertWindow
Registering binding: line
Registering binding: rect
Registering binding: text
Registering binding: cursorText
Registering binding: fillColor
Registering binding: lineColor
Registering binding: image
Registering binding: font
Registering binding: additiveBlending
Registering binding: modifyBrush
Registering binding: revertBrush
Registering binding: beginTriangles
Registering binding: endTriangles
Registering binding: textureCoord
Registering binding: vertex
Registering binding: mouse
Registering binding: mouseButton
Registering binding: cursor
Registering binding: key
Registering binding: rawKey
Registering binding: bind
Registering binding: binding
Registering binding: catchKey
Registering binding: keyName
Registering binding: keyCode
Registering binding: modifiedKey
Registering binding: millis
Registering binding: micros
Registering binding: musicVolume
Registering binding: musicFade
Registering binding: soundVolume
Registering binding: sound
Registering binding: music
Registering binding: store
Registering binding: retrieve
Registering binding: guiMoveDown
Registering binding: guiMoveRight
Registering binding: guiMoveUp
Registering binding: guiMoveLeft
Registering binding: guiStripFill
Registering binding: guiStripBorder
Registering binding: guiNewStrip
Registering binding: guiPreviousStrip
Registering binding: guiOriginStrip
Registering binding: guiText
Registering binding: guiImage
Registering binding: guiBeginButton
Registering binding: guiEndButton
Registering binding: guiButtonUpBorder
Registering binding: guiButtonOverBorder
Registering binding: guiButtonDownBorder
Registering binding: compress
Registering binding: decompress
Registering binding: hash
Registering binding: encrypt
Registering binding: decrypt
Bindings registered
Default font loaded: /usr/share/mirthkit/DejaVuSans.ttf,12
Downloading remote Squirrel flow: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/main.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/main.nut)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/main.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/main.nut)
Entering downloaded remote Squirrel flow: /home/wingnux/.mirthkit/cache/arcade.mirthkit.com/arcade.py/Arcade/script/main.nut
doNut([http://arcade.mirthkit.com/arcade.nut](http://arcade.mirthkit.com/arcade.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.nut](http://arcade.mirthkit.com/arcade.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/preload.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/preload.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/preload.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/preload.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/include.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/include.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/include.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/include.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Dycolor.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Dycolor.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Dycolor.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Dycolor.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Dyloc.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Dyloc.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Dyloc.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Dyloc.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Dynum.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Dynum.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Dynum.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Dynum.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Box.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Box.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Box.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Box.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Area.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Area.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Area.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Area.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Link.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Link.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Link.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Link.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/FlowDown.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/FlowDown.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/FlowDown.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/FlowDown.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/FlowRight.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/FlowRight.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/FlowRight.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/FlowRight.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/FlowLeft.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/FlowLeft.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/FlowLeft.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/FlowLeft.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/FlowUp.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/FlowUp.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/FlowUp.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/FlowUp.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/CenterX.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/CenterX.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/CenterX.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/CenterX.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/CenterY.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/CenterY.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/CenterY.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/CenterY.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Top.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Top.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Top.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Top.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Left.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Left.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Left.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Left.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Right.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Right.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Right.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Right.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Bottom.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Bottom.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Bottom.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Bottom.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Text.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Text.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Text.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Text.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Image.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Image.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Image.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Image.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Button.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Button.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Button.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Button.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/ButtonColorizer.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/ButtonColorizer.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/ButtonColorizer.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/ButtonColorizer.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/ScrollerArea.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/ScrollerArea.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/ScrollerArea.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/ScrollerArea.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/EditBox.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/EditBox.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/EditBox.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/EditBox.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/PasswordBox.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/PasswordBox.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/PasswordBox.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/PasswordBox.nut)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutButtonB.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutButtonB.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutButtonBL.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutButtonBL.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutButtonBR.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutButtonBR.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutButtonC.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutButtonC.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutButtonR.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutButtonR.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutButtonL.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutButtonL.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutButtonT.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutButtonT.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutButtonTR.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutButtonTR.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutButtonTL.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutButtonTL.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutEditB.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutEditB.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutEditBL.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutEditBL.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutEditBR.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutEditBR.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutEditC.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutEditC.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutEditR.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutEditR.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutEditL.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutEditL.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutEditT.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutEditT.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutEditTR.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutEditTR.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutEditTL.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutEditTL.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutB.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutB.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutBL.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutBL.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutBR.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutBR.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutC.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutC.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutR.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutR.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutL.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutL.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutT.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutT.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutTR.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutTR.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutTL.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutTL.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/up.wav](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/up.wav)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/down.wav](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/down.wav)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/Background.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/Background.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/Background.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/Background.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/GameBox.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/GameBox.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/GameBox.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/GameBox.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/GameList.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/GameList.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/GameList.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/GameList.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/LoginBox.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/LoginBox.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/LoginBox.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/LoginBox.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/WelcomeBox.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/WelcomeBox.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/WelcomeBox.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/WelcomeBox.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/AnnonGUI.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/AnnonGUI.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/AnnonGUI.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/AnnonGUI.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/states.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/states.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/states.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/states.nut)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/data/DejaVuSans.ttf](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/data/DejaVuSans.ttf)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/data/MirthKitBig.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/data/MirthKitBig.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py/images?k=0&game=/FinityFlight](http://arcade.mirthkit.com/arcade.py/images?k=0&game=/FinityFlight)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/RegisterBox.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/RegisterBox.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/RegisterBox.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/RegisterBox.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/ErrorBox.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/ErrorBox.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/ErrorBox.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/ErrorBox.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/MenuBox.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/MenuBox.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/MenuBox.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/MenuBox.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/AllGamesGUI.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/AllGamesGUI.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/AllGamesGUI.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/AllGamesGUI.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/MyGamesGUI.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/MyGamesGUI.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/MyGamesGUI.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/MyGamesGUI.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/InfoGUI.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/InfoGUI.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/InfoGUI.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/InfoGUI.nut)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/data/fade.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/data/fade.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/data/shape.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/data/shape.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/data/DejaVuSans-BoldOblique.ttf](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/data/DejaVuSans-BoldOblique.ttf)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/script/main.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/script/main.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/script/main.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/script/main.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/script/preload.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/script/preload.nut))
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/script/preload.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/script/preload.nut)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/DejaVuSerif-BoldOblique.ttf](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/DejaVuSerif-BoldOblique.ttf)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/f500.ttf](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/f500.ttf)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/venusris](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/venusris)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/BlasterShot.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/BlasterShot.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/BlasterShot2bottom.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/BlasterShot2bottom.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/BlasterShot2top.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/BlasterShot2top.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Cloud1.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Cloud1.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/clouds.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/clouds.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/debris.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/debris.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/flare.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/flare.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Gnat.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Gnat.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/ground.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/ground.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/GunDrone.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/GunDrone.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Help.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Help.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Hoplite.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Hoplite.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Janus.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Janus.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/JanusLeft.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/JanusLeft.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/JanusRight.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/JanusRight.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/JanusTurret.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/JanusTurret.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Laser.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Laser.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/LaserCannon.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/LaserCannon.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/loadybar.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/loadybar.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/loadybarBase.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/loadybarBase.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/loadybarCap.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/loadybarCap.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Mercury.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Mercury.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/NaiadBase.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/NaiadBase.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/NaiadProp.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/NaiadProp.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/NaiadTurret.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/NaiadTurret.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/overclouds.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/overclouds.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Raptor.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Raptor.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Regulus.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Regulus.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/reticle.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/reticle.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Rocket.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Rocket.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Rockets.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Rockets.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/shield.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/shield.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/shockwave.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/shockwave.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Sky.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Sky.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/smoke.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/smoke.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/sparkle.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/sparkle.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/track.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/track.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Vulcan.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Vulcan.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/VulcanFlash1.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/VulcanFlash1.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/VulcanFlash2.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/VulcanFlash2.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/VulcanFlash3.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/VulcanFlash3.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/VulcanShot1.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/VulcanShot1.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/VulcanShot2.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/VulcanShot2.png)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/blaster.wav](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/blaster.wav)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/blaster2.wav](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/blaster2.wav)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/boost.wav](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/boost.wav)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/explosion.wav](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/explosion.wav)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/laser.wav](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/laser.wav)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Rocket.wav](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Rocket.wav)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/vulcan.wav](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/vulcan.wav)
Downloading URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/one.ogg](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/one.ogg)
Floating point exception
wingnux@wingnux-desktop ~ $ 


---

### Post by curvedinfinity on 2008-08-08
It appears that SDL_mixer, libogg, libvorbis, or libvorbisfile is doing something funky. Are your versions the latest?

-- If they are, I'll have to look into what's happening a bit more. Libraries are such a pain! ;)

Thanks much!

---

### Post by wingnux on 2008-08-11
Yeap, my system is always up-to-date ;)

---

### Post by curvedinfinity on 2008-08-12
Wingnux, hmmm... if you're ubuntu is basically the same as mine (which if it's 8.04 like me, it is), then my only guess without more specific info on what's happening (MK has far from leet debugging info in the console) is...
```

mirthkit -fresh

```
Which deletes your disk-cache. -- I'm betting that somehow it downloaded an ugly .ogg, which was crashing the library...

---

### Post by Crafty Kisses on 2008-08-12
This game actually looks pretty cool, I'm going to install later on. Thanks!

---

### Post by wingnux on 2008-08-12
I'd previously deleted the disk cache to see if it could help but it didn't, neither did the "-fresh" parameter :P

---

### Post by curvedinfinity on 2008-08-12
Heya, I think I fixed the crash, but not the ogg loading...

[http://storage.mirthkit.com/mirthkit_1.1-3.deb](http://storage.mirthkit.com/mirthkit_1.1-3.deb)

Hopefully you'll be able to play the game -- just no music.

---

### Post by wingnux on 2008-08-13
I give up :P

> wingnux@wingnux-desktop ~/Downloads/epsxe $ mirthkit -debug
Initializing client...
Retrieved window size preference: 800x600
Initialized Squirrel
Initialized curl
Initializing MirthKit subsystems...
Initializing amaryllis subsystem
Initializing albillo subsystem
Initializing andromeda subsystem
Initializing MirthKit subsystems complete
Initialization complete
Registering Squirrel bindings...
Registering binding: update
Registering binding: screen
Registering binding: flush
Registering binding: srand
Registering binding: version
Registering binding: loadNut
Registering binding: doNut
Registering binding: http
Registering binding: progress
Registering binding: open
Registering binding: close
Registering binding: send
Registering binding: receive
Registering binding: background
Registering binding: modifyWindow
Registering binding: revertWindow
Registering binding: line
Registering binding: rect
Registering binding: text
Registering binding: cursorText
Registering binding: fillColor
Registering binding: lineColor
Registering binding: image
Registering binding: font
Registering binding: additiveBlending
Registering binding: modifyBrush
Registering binding: revertBrush
Registering binding: beginTriangles
Registering binding: endTriangles
Registering binding: textureCoord
Registering binding: vertex
Registering binding: mouse
Registering binding: mouseButton
Registering binding: cursor
Registering binding: key
Registering binding: rawKey
Registering binding: bind
Registering binding: binding
Registering binding: catchKey
Registering binding: keyName
Registering binding: keyCode
Registering binding: modifiedKey
Registering binding: millis
Registering binding: micros
Registering binding: musicVolume
Registering binding: musicFade
Registering binding: soundVolume
Registering binding: sound
Registering binding: music
Registering binding: store
Registering binding: retrieve
Registering binding: guiMoveDown
Registering binding: guiMoveRight
Registering binding: guiMoveUp
Registering binding: guiMoveLeft
Registering binding: guiStripFill
Registering binding: guiStripBorder
Registering binding: guiNewStrip
Registering binding: guiPreviousStrip
Registering binding: guiOriginStrip
Registering binding: guiText
Registering binding: guiImage
Registering binding: guiBeginButton
Registering binding: guiEndButton
Registering binding: guiButtonUpBorder
Registering binding: guiButtonOverBorder
Registering binding: guiButtonDownBorder
Registering binding: compress
Registering binding: decompress
Registering binding: hash
Registering binding: encrypt
Registering binding: decrypt
Bindings registered
Default font loaded: /usr/share/mirthkit/DejaVuSans.ttf,12
Downloading remote Squirrel flow: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/main.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/main.nut)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/main.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/main.nut)
Entering downloaded remote Squirrel flow: /home/wingnux/.mirthkit/cache/arcade.mirthkit.com/arcade.py/Arcade/script/main.nut
doNut([http://arcade.mirthkit.com/arcade.nut](http://arcade.mirthkit.com/arcade.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.nut](http://arcade.mirthkit.com/arcade.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/preload.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/preload.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/preload.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/preload.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/include.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/include.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/include.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/include.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Dycolor.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Dycolor.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Dycolor.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Dycolor.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Dyloc.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Dyloc.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Dyloc.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Dyloc.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Dynum.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Dynum.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Dynum.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Dynum.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Box.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Box.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Box.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Box.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Area.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Area.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Area.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Area.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Link.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Link.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Link.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Link.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/FlowDown.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/FlowDown.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/FlowDown.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/FlowDown.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/FlowRight.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/FlowRight.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/FlowRight.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/FlowRight.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/FlowLeft.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/FlowLeft.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/FlowLeft.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/FlowLeft.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/FlowUp.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/FlowUp.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/FlowUp.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/FlowUp.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/CenterX.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/CenterX.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/CenterX.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/CenterX.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/CenterY.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/CenterY.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/CenterY.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/CenterY.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Top.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Top.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Top.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Top.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Left.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Left.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Left.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Left.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Right.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Right.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Right.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Right.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Bottom.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Bottom.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Bottom.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Bottom.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Text.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Text.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Text.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Text.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Image.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Image.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Image.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Image.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Button.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Button.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Button.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/Button.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/ButtonColorizer.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/ButtonColorizer.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/ButtonColorizer.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/ButtonColorizer.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/ScrollerArea.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/ScrollerArea.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/ScrollerArea.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/ScrollerArea.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/EditBox.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/EditBox.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/EditBox.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/EditBox.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/PasswordBox.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/PasswordBox.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/PasswordBox.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/script/PasswordBox.nut)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutButtonB.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutButtonB.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutButtonBL.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutButtonBL.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutButtonBR.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutButtonBR.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutButtonC.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutButtonC.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutButtonR.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutButtonR.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutButtonL.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutButtonL.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutButtonT.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutButtonT.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutButtonTR.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutButtonTR.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutButtonTL.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutButtonTL.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutEditB.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutEditB.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutEditBL.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutEditBL.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutEditBR.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutEditBR.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutEditC.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutEditC.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutEditR.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutEditR.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutEditL.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutEditL.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutEditT.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutEditT.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutEditTR.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutEditTR.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutEditTL.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutEditTL.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutB.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutB.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutBL.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutBL.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutBR.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutBR.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutC.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutC.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutR.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutR.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutL.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutL.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutT.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutT.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutTR.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutTR.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutTL.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/skins/CutTL.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/up.wav](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/up.wav)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/down.wav](http://arcade.mirthkit.com/arcade.py?k=0&f=/Library/BetterGUI/data/down.wav)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/Background.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/Background.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/Background.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/Background.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/GameBox.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/GameBox.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/GameBox.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/GameBox.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/GameList.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/GameList.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/GameList.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/GameList.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/LoginBox.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/LoginBox.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/LoginBox.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/LoginBox.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/WelcomeBox.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/WelcomeBox.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/WelcomeBox.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/WelcomeBox.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/AnnonGUI.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/AnnonGUI.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/AnnonGUI.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/AnnonGUI.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/states.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/states.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/states.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/states.nut)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/data/DejaVuSans.ttf](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/data/DejaVuSans.ttf)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/data/MirthKitBig.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/data/MirthKitBig.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py/images?k=0&game=/FinityFlight](http://arcade.mirthkit.com/arcade.py/images?k=0&game=/FinityFlight)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/RegisterBox.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/RegisterBox.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/RegisterBox.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/RegisterBox.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/ErrorBox.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/ErrorBox.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/ErrorBox.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/ErrorBox.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/MenuBox.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/MenuBox.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/MenuBox.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/MenuBox.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/AllGamesGUI.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/AllGamesGUI.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/AllGamesGUI.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/AllGamesGUI.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/MyGamesGUI.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/MyGamesGUI.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/MyGamesGUI.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/MyGamesGUI.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/InfoGUI.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/InfoGUI.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/InfoGUI.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/script/InfoGUI.nut)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/data/fade.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/data/fade.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/data/shape.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/data/shape.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/data/DejaVuSans-BoldOblique.ttf](http://arcade.mirthkit.com/arcade.py?k=0&f=/Arcade/data/DejaVuSans-BoldOblique.ttf)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/script/main.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/script/main.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/script/main.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/script/main.nut)
doNut([http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/script/preload.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/script/preload.nut))
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/script/preload.nut](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/script/preload.nut)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/DejaVuSerif-BoldOblique.ttf](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/DejaVuSerif-BoldOblique.ttf)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/f500.ttf](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/f500.ttf)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/venusris](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/venusris)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/BlasterShot.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/BlasterShot.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/BlasterShot2bottom.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/BlasterShot2bottom.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/BlasterShot2top.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/BlasterShot2top.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Cloud1.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Cloud1.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/clouds.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/clouds.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/debris.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/debris.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/flare.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/flare.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Gnat.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Gnat.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/ground.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/ground.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/GunDrone.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/GunDrone.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Help.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Help.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Hoplite.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Hoplite.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Janus.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Janus.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/JanusLeft.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/JanusLeft.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/JanusRight.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/JanusRight.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/JanusTurret.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/JanusTurret.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Laser.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Laser.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/LaserCannon.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/LaserCannon.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/loadybar.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/loadybar.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/loadybarBase.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/loadybarBase.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/loadybarCap.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/loadybarCap.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Mercury.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Mercury.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/NaiadBase.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/NaiadBase.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/NaiadProp.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/NaiadProp.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/NaiadTurret.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/NaiadTurret.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/overclouds.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/overclouds.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Raptor.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Raptor.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Regulus.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Regulus.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/reticle.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/reticle.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Rocket.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Rocket.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Rockets.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Rockets.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/shield.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/shield.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/shockwave.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/shockwave.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Sky.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Sky.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/smoke.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/smoke.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/sparkle.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/sparkle.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/track.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/track.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Vulcan.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Vulcan.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/VulcanFlash1.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/VulcanFlash1.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/VulcanFlash2.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/VulcanFlash2.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/VulcanFlash3.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/VulcanFlash3.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/VulcanShot1.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/VulcanShot1.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/VulcanShot2.png](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/VulcanShot2.png)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/blaster.wav](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/blaster.wav)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/blaster2.wav](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/blaster2.wav)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/boost.wav](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/boost.wav)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/explosion.wav](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/explosion.wav)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/laser.wav](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/laser.wav)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Rocket.wav](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/Rocket.wav)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/vulcan.wav](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/vulcan.wav)
Using cached URL: [http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/one.ogg](http://arcade.mirthkit.com/arcade.py?k=0&f=/FinityFlight/data/one.ogg)
Floating point exception

---

### Post by anotherconfused1 on 2008-08-13
Works great on my 32bit Hardy!

---

### Post by curvedinfinity on 2008-08-13
Gosh, sorry I couldn't get it running for you, wingnux. I've got it listed as a bug, so hopefully it will get resolved eventually. ;)

---

### Post by wingnux on 2008-08-15
No problem, feel free to PM me if you need any debugging info ;)

---

### Post by mikedep333 on 2008-08-16
Hey. I just ran it on Windows and it was a lot of fun. Great job. It is great to see professionally produced games as open source, and commercial games come with the source available for modification.

Do you plan on improving finity flight and producing more open source or commercial games, or is finity flight merely a test/example for MirthKit?

BTW, mirthkit is much prettier than steam.

---

### Post by curvedinfinity on 2008-08-16
@ mikedep333: Hey, thanks for the compliments! We're actually in the works of producing a patch for Finity Flight, which mainly has usibility improvements, but also has some other small fixes and additions. In addition to that, we're also making an expansion for Finity Flight which includes some new enemies, a new setting, and bosses. We will most definitely be making more games in the future from a wide variety of genres.

Currently planned, we have [Tower of Ios]("http://forum.mirthkit.com/viewtopic.php?id=9")

And much more excitingly, an internet coop platformer with the working title "Block Game". This game is two player. One player controls a more traditional platformer character called "The Guy", where the other player controls what we call "The God" (that name may change, hehe). The God's responsibility it to create the level in front of the The Guy, so The Guy can reach objectives and replenish The God's ability to manipulate the level. -- This one I'm very excited to see how it turns out. :)

---

### Post by desertboy on 2008-08-17
Nice one, works fine for me, never bothered installing through terminal so can't tell you if kicked up any error messages.

Game's pretty good, it takes a little while to get used to the mouse aiming but when you d it's great.

---

### Post by punong_bisyonaryo on 2008-09-09
Hi! I've been playing Finity Flight thru MirthKit and having a great time, although I still don't get some of the controls and powerup system. It would be nice if there was some sort of tutorial level or page or something. Also, I didn't notice much difference between levels. Despite all that, Finity Flight is an excellent game, with nice polish. It doesn't feel half-baked like most other OSS games and I'm looking to see what else can be downloaded via MirthKit, as soon as I register.

PS. I noticed MK is closed-source. Closed source gives me a bit of a scare, although I still think that MirthKit is a promising platform to develop for.

PPS. I really like the navigation control with the mouse.

---

### Post by curvedinfinity on 2008-09-09
Hey, thanks alot! We're going to be putting out a patch sometime soon which focuses on the problems you mentioned... so, we're working on it! :)

We actually have three other games in development too, so I'm hoping you'll have some more good games to play soon.

---

### Post by lukjad on 2008-09-09
Thanks, I'll check it out.

---

### Post by punong_bisyonaryo on 2008-09-11
I've got a little problem registering with MirthKit -- it doesn't seem to accept some symbols such as the "_" of my email address...

Is there another way of registering?

---

### Post by curvedinfinity on 2008-09-11
That's a bug I wasn't aware of, actually. I'll get that one fixed. Just so you know, anyway, there are no other games available quite yet.

---

### Post by Marsan on 2008-09-11
Hey.

I cant install the game. Im on Gutsy 32bit and both .deb`s mirthkit_1.1-3 and mirthkit_1.1-2 fails to install because of dependecies. (See pic).

The installer complains that the package libsdl1.2debian is not installed, but i cheked, and it is installed. Any help here?

BTW. The windows-installer through wine works, but the game wont run.

---

### Post by curvedinfinity on 2008-09-11
Hey Marsan,
You're going to have to get the newer versions of those libraries than the ones Gutsy supports. The easiest way to do that is to hunt them down on Hardy's launchpad...

[https://code.launchpad.net/ubuntu/hardy](https://code.launchpad.net/ubuntu/hardy)

Hope this helps!

---

### Post by punong_bisyonaryo on 2008-09-11
> **curvedinfinity said:**
> That's a bug I wasn't aware of, actually. I'll get that one fixed. Just so you know, anyway, there are no other games available quite yet.

Appreciate the effort. Are there any planned releases of new games yet, either from you or third-party indie OSS game makers?

---

### Post by curvedinfinity on 2008-09-11
As far as "us," I just posted this preview of "Finity Flight: Fight Back"...

[http://ubuntuforums.org/showthread.php?t=917195](http://ubuntuforums.org/showthread.php?t=917195)

Also, I'm personally working on a game called "Tower of Ios", which is a new puzzle concept...

[http://forum.mirthkit.com/viewtopic.php?id=22](http://forum.mirthkit.com/viewtopic.php?id=22)

Lastly, after Fight Back is released, the team is working toward designing a simple multiplayer game. :)

As far as 3rd parties, a fellow on our forums seems very keen about an MMO based off of some distributed tech I've been working on (just talk currently, though)...
[http://forum.mirthkit.com/viewforum.php?id=11](http://forum.mirthkit.com/viewforum.php?id=11)

A good friend of mine has been working on another puzzle game also.

---

### Post by binbash on 2008-09-12
Wow it crashes everytime i couldn't start the game : ) The Gui is SOOOO buggy.Register screen sucks because you can't put that damn @ to e-mail section.But i guess the project will be cool.

---

### Post by meborc on 2008-09-12
really cool game... no problems playing on ubuntu intrepid alpha :D

---

### Post by punong_bisyonaryo on 2008-10-07
Hey there!

I tried registering today, after downloading the latest MirthKit. It now accepts underscores and the "@" sign. Woohoo!

Still wasn't able to register though, my email address is too long. Maybe in the next release you could make the limit longer? (Hint: My email address is 27 characters long. There MIGHT be a longer email address out there though. Didn't check the username/password limits).

---

