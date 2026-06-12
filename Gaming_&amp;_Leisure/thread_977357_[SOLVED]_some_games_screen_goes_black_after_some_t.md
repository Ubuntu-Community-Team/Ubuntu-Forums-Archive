---
title: "[SOLVED] some games screen goes black after some time"
date: 2008-11-10
forum: Gaming &amp; Leisure
---

### Post by LordIshamael on 2008-11-10
hey i have a toshiba u300 111 w/ kubuntu intrepid
certain games such as openarena, supertux and warzone have problems
i start up, play for maybe half a minute, then the screen goes partly black
as in i can still see some details eg. in openarena i can see the basic outline and movement of some players, as well as some glowing icons, but its as if the entire game has been 'lights off' sort of...
i dont think ths is an intrepid issue as i had the supertux problem from hardy...
my lspci shows my vga controller as intel mobile gm965/gl960
is this a graphics driver problem?i read somewhere that there are no proprietary drivers available for intel for linux, the opengl ones are the only ones there are, and hardware drivers shows no proprietary drivers installed...
if it is a graphics card problem, can i get better graphics cards? i read that its not possible to change the graphics cards of certain laptopts, if its integrated w/ the motherboard
if not, then whats the issue and how can i resolve it?
any help is greatly appreciated...
thanks

---

### Post by dreamer84 on 2008-11-10
hi,
my notebook had these issues even on gnome, maybe it's the energy saving setting. I fixed this by changing the energy setting for darkening the screen (sorry, dunno the exact english name) to "never". Probably games prevent gnome from knowing that keys are pressed, so it thinks it's inactive (e.g. I can't change sound volume with the notebook keys while playing).
If you're unsure about your graphics, run a terminal and enter ```
glxinfo | grep render
``` and check if direct rendering is "yes", it should be fine then.

---

### Post by LordIshamael on 2008-11-11
yep, glxinfo gives 'yes'

the power settings on my laptopt are to dim display after 20 mins, but it usually goes black before...
ill give it a try anyway, disabled the dim display option, so ill try out the games now

thanks for the tip!

---

### Post by jerrylamos on 2008-11-11
Intrepid is infamous for problems with compiz on Intel video graphics.  Try System Preferences Visual Effects None.

Jerry

---

### Post by sharon.gmc on 2008-11-12
i actually have the same problem. . . .

---

### Post by dreamer84 on 2008-11-12
> **LordIshamael said:**
> yep, glxinfo gives 'yes'
that should mean your driver is ok

> the power settings on my laptopt are to dim display after 20 mins, but it usually goes black before...
ill give it a try anyway, disabled the dim display option, so ill try out the games now
did it work? my laptop also had the 20 min setting and still it dimmed after 2 mins... maybe your ubuntu also doesn't properly recognize whether you are in battery mode?

[QUOTE=jerrylamos]Intrepid is infamous for problems with compiz on Intel video graphics. Try System Preferences Visual Effects None.[/QUOTE]
right, I remember another thread (something about ut2003 or 2004) where the suggestion was a script to call the game while disabling compiz:
```

metacity --replace && sleep 3
yourgamehere
compiz --replace && sleep 3
```
one side-effect was the possibility of enabled antialiasing on gnome...

---

### Post by LordIshamael on 2008-11-12
yep, tried the suggestion of changing dim settings
didnt work, it still goes darker, and waaay before 20 mins
most of my compiz settings will not be enabled anyway as i have copizconfigsettingsmanager uninstalled, but ill give the disabling visual effects a shot

and no, ubuntu has no problem recognising when im on battery or a/c

---

### Post by LordIshamael on 2008-11-12
@jerry

worked like a charm

thanks a lot!

---

