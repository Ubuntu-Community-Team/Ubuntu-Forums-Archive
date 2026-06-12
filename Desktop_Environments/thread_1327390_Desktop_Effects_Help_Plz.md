---
title: "Desktop Effects Help Plz"
date: 2009-11-15
forum: Desktop Environments
---

### Post by demorik on 2009-11-15
I would appreciate if anyone could help me, im using ubuntu 9.04 on a presario c564us laptop and i cant enable desktop effects and also everything looks like the wrong aspect ratio, i read a post where i entered a command and i didnt see "backlisted" in the result. Please if anyone could help thanks.

---

### Post by stinkeye on 2009-11-15
[COLOR="DarkRed"]EDIT:[/COLOR] HAVE A LOOK AT LINK AT BOTTOM FIRST.

I don't know if there's any specific problem with your computer.
But to enable desktop effects:
 open system > administration > hardware drivers
it will search for drivers and if found click on the recommended driver
and activate.
Then restart your computer.

Open system > preferences > appearance > visual effects
and click on extra.
To configure compiz effects install compizconfig-settings-manager and fusion-icon.
Add fusion-icon to  startup applications using 
```
fusion-icon -n
```
in the command box. -n loads fusion without trying to load a window manager
because it can cause problems.

This page might be of more specific help:
[_[COLOR="DarkRed"]http://www.uluga.ubuntuforums.org/showthread.php?t=1311885[/COLOR]_]("http://www.uluga.ubuntuforums.org/showthread.php?t=1311885")

---

### Post by andrea000 on 2009-11-15
What's your video card?You said you ran a command and
didn't see blacklisted? was it compiz ran from the
terminal if not try that also you can run compiz check
there is a link at the bottom of my post.

---

### Post by demorik on 2009-11-15
I was away for while so i forgot the command, but it listed my hardware i think, from the live cd i can run compiz, after instal no. When i try to enable it says cannot enable desktop effects, when i search for hardware it only gives me the wireless driver but no graphics, i heard there is a way to force it, does that work? or should i just forget compiz?

---

### Post by wojox on 2009-11-15
Open a terminal and run:

```
lspci | grep VGA
```

and post back the results.

---

### Post by demorik on 2009-11-15
Guys for some reason i reinstalled ubuntu and effects started working without any graphics install or anything, all effects working now i can even set the correct screen resolution. Thank u all for your time.

---

