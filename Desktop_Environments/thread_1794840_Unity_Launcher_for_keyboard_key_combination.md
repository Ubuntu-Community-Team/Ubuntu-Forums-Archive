---
title: "Unity Launcher for keyboard key combination"
date: 2011-07-01
forum: Desktop Environments
---

### Post by EgoGratis on 2011-07-01
Is it possible to create custom Unity Launcher that would do the same thing as pressing some keys on the keyboard.

Thanks!

---

### Post by kerry_s on 2011-07-01
yes, you need xvkbd & then you just use main menu to make. once it's showing in dash just drag & drop on unity launcher.

wait, i think it's not xvkbd, i forget the name of the program right now. will put later if i remember.

it's "xdotool".
 xvkbd can using -xsendevent, but xdotool is much easier.

example:
xdotool key Ctrl+Alt+Right

use "man xdotool" to learn more.

---

### Post by EgoGratis on 2011-07-01
Fantastic, just what i need, but i do have one problem:

If i create test launcher in ~/.local/share/applications/test.desktop and put this in it:

```
[Desktop Entry]
Name=test
Comment=
Exec=xdotool key "Ctrl+Alt+Right"
Icon=desktop
Terminal=false
Type=Application
StartupNotify=true
```I can drag it to launcher from that folder (from dash it does not work, probably bug) and run it and it works! But it only works once. Any help?

---

### Post by kerry_s on 2011-07-01
perhaps it's not exiting cause your running the command instead of a script.

in a terminal type-> killall xdotool

then try the launcher, if it works then you know, you need to move it to a script & exit it properly.

---

### Post by wildmanne39 on 2011-07-02
> **EgoGratis said:**
> Fantastic, just what i need, but i do have one problem:

If i create test launcher in ~/.local/share/applications/test.desktop and put this in it:

```
[Desktop Entry]
Name=test
Comment=
Exec=xdotool key "Ctrl+Alt+Right"
Icon=desktop
Terminal=false
Type=Application
StartupNotify=true
```I can drag it to launcher from that folder (from dash it does not work, probably bug) and run it and it works! But it only works once. Any help?Hi, click on the power user guide in my signature and it will give you instructions for creating launchers.

---

### Post by stinkeye on 2011-07-02
> **EgoGratis said:**
> Fantastic, just what i need, but i do have one problem:

If i create test launcher in ~/.local/share/applications/test.desktop and put this in it:

```
[Desktop Entry]
Name=test
Comment=
Exec=xdotool key "Ctrl+Alt+Right"
Icon=desktop
Terminal=false
Type=Application
StartupNotify=true
```I can drag it to launcher from that folder (from dash it does not work, probably bug) and run it and it works! But it only works once. Any help?

It works here but as with all launchers, once clicked it won't be usable
again for about 10 seconds(while the icon is pulsing).
You can use middle click during this time to run again.

---

### Post by EgoGratis on 2011-07-02
> in a terminal type-> killall xdotool

then try the launcher, if it works then you know, you need to move it to a script & exit it properly.

xdotool: no process found

> It works here but as with all launchers, once clicked it won't be usable
again for about 10 seconds(while the icon is pulsing).
You can use middle click during this time to run again.

It is not usable no mater how much time i wait. But yes middle click always works. :p

> Hi, click on the power user guide in my signature and it will give you instructions for creating launchers.

Thanks for the info. I will try to put together all the information from this thread later on and i will post updates!

---

### Post by EgoGratis on 2011-07-02
I tried to find solution for left clicking more then one time but i didn't find nothing. It only works once. But OK at least middle mouse buttons work all the time and that is still great! Thanks you all for helping with informations.

---

### Post by fishbulb1022 on 2011-07-24
Looks like you've already got something working, but for future reference you could try xte from the xautomation package. I used it to make a unity launcher for the scale plugin and it it works great. I think it might help with your issues where the launcher only worked once.

---

### Post by EgoGratis on 2011-07-25
**Thanks @fishbulb1022 it does work! **

There is just one more "glitch" i am not able to solve. If i start up for example Nautilus the animation in Launcher stops very quickly and if i quickly close Nautilus i can open new one very fast.

But with custom Launcher the animation just goes on and on for about 5 seconds. This five seconds only middle mouse button works.

Is there a way, to reduce this "animation" time to 0? There has to be some mechanism behind this because Nautilus as soon it is loaded the animation stops and as soon as i close Nautilus i can use left mouse button on Launcher to open Nautilus again. It does not have to be 5 seconds in between. I have to convince the launcher "xte" has loaded and it was closed in "split second". Is this possible and how would i do that?

---

