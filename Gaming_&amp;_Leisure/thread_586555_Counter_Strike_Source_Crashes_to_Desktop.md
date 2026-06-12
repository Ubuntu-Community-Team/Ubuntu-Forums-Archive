---
title: "Counter Strike: Source Crashes to Desktop"
date: 2007-10-22
forum: Gaming &amp; Leisure
---

### Post by KnightGeek on 2007-10-22
Counter Strike: Source starts from steam, but refuses to get past the loading screen. I have noticed that there is a message on screen if I close the desktop window, but I can't get a good look at it. It's there for half a second, then gone.
[IMG]http://static.zooomr.com/images/3565768_d94bbef374.jpg?r=360[/IMG]

---

### Post by esodin on 2007-10-22
Check out[COLOR="Red"] [ this tread]("http://ubuntuforums.org/showthread.php?t=585966")[/COLOR]

---

### Post by KnightGeek on 2007-10-22
Those are all good suggestions, but I tried most and they didn't work. The command line start-up command didn't work for me either. :(

---

### Post by aoanla on 2007-10-22
Do you, by any chance, have an ATI graphics card? The fglrx driver seems to have some kind of issue with wine 0.9.46 and wine 0.9.47 - the people having the most problems with Source games under those versions of wine all seem to have ATI cards.

If it were possible to regress further, I'd suggest compiling wine 0.9.42 for Gutsy, or waiting until the new fglrx driver release sometime this week, as that might improve matters too.

---

### Post by KnightGeek on 2007-10-22
That would explain a lot! I have a Radeon X1650! I'll probably wait out the driver. If that doesn't work, I'll compile the older version of wine (though I like the uninstaller and menu for the latest version). Thanks for the help! Linux on!!!:guitar:

---

