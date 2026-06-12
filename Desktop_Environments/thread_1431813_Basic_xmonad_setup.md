---
title: "Basic xmonad setup"
date: 2010-03-17
forum: Desktop Environments
---

### Post by Kodpoet on 2010-03-17
Hi,

I've started using xmonad as my window manager and is currently trying to make it effective to use by installing dzen2, a system tray and starting som basic things on startup, such as nm-applet. Now, I've managed to get to a point where both dzen2 and xmonad works, but my start-up script doesn't work the way I want and I haven't found a suitable system tray yet. (Most people seem to use "trayer" which is listed in the repos but has no install candidate)

Now, to the facts:

I followed this tutorial to set up xmonad and dzen2: [http://tombuntu.com/index.php/2009/03/19/adding-a-dzen2-statusbar-to-xmonad/](http://tombuntu.com/index.php/2009/03/19/adding-a-dzen2-statusbar-to-xmonad/)

My setup is basically exactly like his but to the end of the tutorial he mentions that you could start all the apps I need at startup from a startup_script. The startup_script.sh is run from xmonad.desktop and my version looks like this:

```

#!/bin/sh

# Start Xmonad and pipe status data to dzen
xmonad | dzen2 -ta l

# launch terminal
# gnome-terminal

# Allow wireless internet access
# nm-applet

# Set background
feh --bg-scale ~/Pictures/Beautiful.jpg

```The script halts after the first line and never executes the rest of the script, which might be obvious to you if you're experienced in scripting - I am not. :) I'm aware that you can start apps from inside the xmonad.hs config file but somehow I've gotten the idea that it's better to do it in the startup  script, if that's wrong please tell me so. ^^

My questions are as follows:

1. What's wrong with my script and what do I need to make it run my apps?
2. What system tray is best for this setup? (and please point me in the right direction about how to install and set it up)

Thank you for your time and effort!

---

### Post by aeiah on 2010-03-17
usually you put the window manager at the end. also, after each command, you want a '&' so it executes the next one. right now your script is issueing the first command and waiting for it to stop.

try:
```

#!/bin/sh

# Set background
feh --bg-scale ~/Pictures/Beautiful.jpg &

# Allow wireless internet access
# nm-applet &

# launch terminal
# gnome-terminal &

# Start Xmonad and pipe status data to dzen
xmonad | dzen2 -ta l


```

i assume the last command (xmonad..) is correct. usually id start the wm with exec (exec openbox, exec awesome, exec xmonad) but dzen2 seems peculiar and seems to like pipes so its probably fine.

---

### Post by aeiah on 2010-03-17
as for system trays and whatnot.. i like lxpanel, but its very similar to gnome panel.. a lot of openbox users like tint2 i think. there's also pypanel.

if you just want a system tray on its own (or perhaps incorporated into dzen, i dunno) you could take a look at stalonetray

---

### Post by Kodpoet on 2010-03-17
> **aeiah said:**
> usually you put the window manager at the end. also, after each command, you want a '&' so it executes the next one. right now your script is issueing the first command and waiting for it to stop.

try:
```

#!/bin/sh

# Set background
feh --bg-scale ~/Pictures/Beautiful.jpg &

# Allow wireless internet access
# nm-applet &

# launch terminal
# gnome-terminal &

# Start Xmonad and pipe status data to dzen
xmonad | dzen2 -ta l


```i assume the last command (xmonad..) is correct. usually id start the wm with exec (exec openbox, exec awesome, exec xmonad) but dzen2 seems peculiar and seems to like pipes so its probably fine.


Thank you for that, you're absolutely right, it works like a charm! ^^

I'll start looking at the trays. :)

---

### Post by falconindy on 2010-03-17
Put the actual invocation of xmonad in a separate script, such as ~/bin/startxmonad:

```
#!/bin/bash

/usr/bin/xmonad | dzen2 -ta l
```
Then you can use `exec ~/bin/startdwm` as the last line of your '~/.xinitrc'.

Separation of this task lets you do things like:

```
while true; do
    /usr/bin/xmonad | dzen2 -ta l
done
```
This way, you can recompile Xmonad and send a quit signal (shift-mod-q) which won't kill X, but just restart Xmonad with the new config. Keep in mind this means you've now sort of lost the ability to kill X as you normally would, so you need to to either:

a) killall xmonad
b) add a line to your .xinitrc to map ctrl-alt-bksp to terminate the X server: setxbmap -option terminate:ctrl_alt_bksp

Happy tiling!

---

### Post by ibuclaw on 2010-03-17
I've always liked to use xmobar myself, not sure what dzen2 does different though...

---

### Post by falconindy on 2010-03-17
My love for Haskell like a baby seal and a club. I'm the seal.

It's true though. Xmobar is a better match for Xmonad. Also, looks like its possible to restart xmonad without the filthy hack i mentioned. The default config gives this little gem of a keybind:

```
, ((modm              , xK_q     ), spawn "xmonad --recompile; xmonad --restart")
```

---

