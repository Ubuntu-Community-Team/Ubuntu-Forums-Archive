---
title: "unity --reset hangs at Setting Update &quot;fullscreen_visual_bell&quot;"
date: 2011-11-30
forum: Desktop Environments
---

### Post by vt.dave on 2011-11-30
Hey everyone,

I had Ubuntu 11.10 installed with Unity and everything was working great...until I installed ccsm.  I launched ccsm, made 1 tweak to change the launcher bar size, and ccsm locked up (didn't close, desktop hung).

So I rebooted, logged in and the top and side bars were gone, hit Alt+F4 to get to shell, run unity --reset and it hangs at
```
Setting Update "fullscreen_visual_bell"
```

It never passes this point, i can login with Unity 2D and Gnome classic just fine, but I want my fully Unity back :).

I've tried running ccsm again and making sure unity was checked, I've tried force reinstalling all of unity, but nothing seems to work.

Any advice or logs I can look at to try and resolve this?

Thanks.
-Dave

---

### Post by vt.dave on 2011-12-01
bump?

I'm in unity 2d now, but i'd like to fix the issue if possible.

---

### Post by vt.dave on 2011-12-14
double bump?  Problem still persists :(

---

### Post by stinkeye on 2011-12-15
From your 2d session bring up a terminal and use this to
set compiz to defaults and re-enable the unity plugin.
```
gconftool-2 --recursive-unset /apps/compiz-1 && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins [core,bailer,detection,composite,opengl,compiztoolbox,decor,grid,move,resize,mousepoll,regex,snap,gnomecompat,place,imgpng,vpswitch,animation,wall,workarounds,fade,session,expo,ezoom,unityshell]
```
You could also do this by going to **ccsm > preferences** and hitting the default button and then
re-enabling the unity plugin.

Then login to the ubuntu session.

---

### Post by vt.dave on 2011-12-15
> **stinkeye said:**
> From your 2d session bring up a terminal and use this to
set compiz to defaults and re-enable the unity plugin.
```
gconftool-2 --recursive-unset /apps/compiz-1 && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins [core,bailer,detection,composite,opengl,compiztoolbox,decor,grid,move,resize,mousepoll,regex,snap,gnomecompat,place,imgpng,vpswitch,animation,wall,workarounds,fade,session,expo,ezoom,unityshell]
```

This WORKED!!  Thanks so much, nothing else did the trick.  I actually hit Ctrl+Alt+F4 to drop out of all unity stuff and ran that command, rebooted and logged in to unity no problem!


> **stinkeye said:**
> 
You could also do this by going to **ccsm > preferences** and hitting the default button and then
re-enabling the unity plugin.

Then login to the ubuntu session.
Just FYI this did not work...clicking restore defaults, then checking the unity plugin gave me the same "Conflicts Exist" and I clicked ignore, rebooted and when I logged in to unity the top and side bars were gone, that's when I hit Ctrl+Alt+F4 and tried the above command.

Thanks again!

---

### Post by stinkeye on 2011-12-15
> **vt.dave said:**
> This WORKED!!  Thanks so much, nothing else did the trick.  I actually hit Ctrl+Alt+F4 to drop out of all unity stuff and ran that command, rebooted and logged in to unity no problem!



Just FYI this did not work...clicking restore defaults, then checking the unity plugin gave me the same "Conflicts Exist" and I clicked ignore, rebooted and when I logged in to unity the top and side bars were gone, that's when I hit Ctrl+Alt+F4 and tried the above command.

Thanks again!
Did you upgrade or fresh install. If you upgraded that may be where the compiz conflict exists.

---

### Post by vt.dave on 2011-12-15
> **stinkeye said:**
> Did you upgrade or fresh install. If you upgraded that may be where the compiz conflict exists.

I upgraded from 11.04 to 11.10, but everything was peachy until i went into CCSM for the first time to adjust my launcher size, which I'm terrified of trying again :-P

---

### Post by stinkeye on 2011-12-15
> **vt.dave said:**
> I upgraded from 11.04 to 11.10, but everything was peachy until i went into CCSM for the first time to adjust my launcher size, which I'm terrified of trying again :-P
That command will always get you out of any compiz messups.

When you upgrade from 11.04 to 11.10 the old compiz configs mess with 
the different version of ccsm.
The command I gave earlier works because it enables the right plugins for 11.10.
The ccsm method doesn't work because the old configs mess around with the default values and plugins.
For me, the ccsm method works because I did a fresh install, therefore had no old configs.


I would remove all the compiz configs.
Run these commands one at a time then log out/in.
```
rm -rf .gconf/apps/compiz*
rm -rf .cache/compizconfig-1/
rm -rf .config/compiz-1/
rm -rf .compiz*
```
This will make ccsm behave properly.
Even on a fresh install ccsm is a bit buggy... ie it might not load properly after changing a setting
but can usually be fixed by just running, while in the 3d session...
```
compiz --replace & disown
```


If that fails then running the set default command I gave will take you back to default settings again.
The same command can be run within Unity if you can ctl+alt+t to open a terminal.
This set default command adds an extra **compiz --replace & disown** command to
the end to make sure compiz loads properly while in the 3d session.
```
gconftool-2 --recursive-unset /apps/compiz-1 && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins [core,bailer,detection,composite,opengl,compiztoolbox,decor,grid,move,resize,mousepoll,regex,snap,gnomecompat,place,imgpng,vpswitch,animation,wall,workarounds,fade,session,expo,ezoom,unityshell] && compiz --replace & disown
```

---

