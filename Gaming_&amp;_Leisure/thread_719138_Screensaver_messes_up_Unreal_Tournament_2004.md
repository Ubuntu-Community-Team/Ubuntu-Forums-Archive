---
title: "Screensaver messes up Unreal Tournament 2004"
date: 2008-03-08
forum: Gaming &amp; Leisure
---

### Post by Agent ME on 2008-03-08
I recently installed Unreal Tournament 2004 onto my computer after it suffered a lot of neglect, but this time onto my linux 64 bit comp with this tutorial - [http://gaming.gwos.org/doku.php/guides:64bit:ut2004](http://gaming.gwos.org/doku.php/guides:64bit:ut2004)

The game works great, except about every five minutes it seems, the game switches to windowed mode for about 5 seconds, then back to fullscreen, and controls don't work properly for about 20 seconds. I might possibly be hitting some button combination accidentally that is doing it, but I doubt that.

If I leave my computer idle for some time with the game running, the computer should go into screensaver mode, but when I come back I find the screen blank, and nothing I press does anything (except ctrl+alt+ a number to get to other screens). The only way to get out of this is for me to go to a terminal, log in, and reboot from there or use "ps -e", then "kill number" with the number of ut2004-bin-linu's process, then switch back to the #7 screen.

Any ideas for help?

---

### Post by GSZX1337 on 2008-03-08
I would just disable the screen saver Preferences > Screen Saver > uncheck "Activate screensaver when computer is idle"
Screensavers were meant to prevent burn-in for CRTs, but for LCDs, they are unneeded.

---

### Post by Agent ME on 2008-03-08
Is it possible I can edit the ut2004 script to turn off the screensaver when the game starts, and turn it back on on exit?

---

### Post by Perfect Storm on 2008-03-09
It's more likely a combo with compiz+screensaver.

Try this and see if it helps.

<alt>+<F2>
```
metacity --replace
```

now try play ut2004 and see if that's the problem.

---

### Post by Agent ME on 2008-03-09
That fixed it (both problems), but I'd like to have the extra visual effects in my desktop. My idea is that I'd add that command in the ut2004 script that you mentioned, and before exit change it back. What command would I use to change it back so there are the extra visual effects?

---

### Post by Perfect Storm on 2008-03-10
```
cd <where-ever-you-want-the-script>
nano ut2004-launch.sh
```

add:

[b]#!/bin/bash
metacity --replace &
ut2004
compiz --replace &[/b]


save [ctrl]+[o], exit [ctrl]+[x]

```
chmod +x ut2004-launch.sh
alacarte
```

Go to Games and find the ut2004 launcher and modify the command box so it points to ut2004-launch.sh instead.

```
sh <path>/ut2004-launch.sh
```

---

### Post by Agent ME on 2008-03-10
The actual ut2004 file already is a script that starts up the game's binary, so I can just put it in there.

That seems like it would work, but I was playing around with the command (compiz --replace) with a bash terminal, and if I ran that command, and then closed the terminal, it would shut down the compiz thing too, completely screwing the system window-wise, and I'd either have to log off and back on, or try to get into the System -> Preferences -> Appearance menu and click an option there to get it back to normal. If I ran ut2004 from a terminal I'd run into this problem. Any way around this? Or am I just going to have to make a mental note not to ever try to run the game from a bash terminal?

---

### Post by lingenfr on 2008-12-28
I know this is an old thread, but as one who has many, I am getting really sick of unanswered threads here. If you ran the command without the '&' that is the problem. It will work the way the fellow told you. I am going to do the same with mine.

---

### Post by epitaph on 2008-12-29
My UT2004 launcher script is as follows:

```
#!/bin/bash
gconftool-2 --set /apps/gnome-screensaver/idle_activation_enabled --type bool 0 &
metacity --replace &
ut2004
killall -9 compiz.real &
compiz --replace &
gconftool-2 --set /apps/gnome-screensaver/idle_activation_enabled --type bool 1 &
```

I will note that, for some reason, the screensaver sometimes does not start after the game has been run. There seems to be little logic to when it does or does not. To fix it, I force the screensaver to start then it works fine:

```
xdg-screensaver activate
```

---

