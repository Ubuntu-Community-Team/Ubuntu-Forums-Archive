---
title: "Running script in gnome-terminal vs. gnome application launcher"
date: 2009-05-11
forum: General Help
---

### Post by fermulator on 2009-05-11
Here's a kicker for someone:

I have a script to launch Warcraft III in WINE.  Executing the script from "gnome-terminal" works great! (the game loads in WINE, no lag, perfect game play)

However, as soon as I try to run the script from the panel (gnome application launcher) .. war3 opens, but is REALLY LAGGY... how is executing from gnome-launcher any different than directly in the command line?

I've been in IRC a little bit and some suggested that the environment variables are different between these two scenarios... potentially the problem?

---

### Post by LoloftheRings on 2009-05-11
I guess it might be the -opengl command argument.
In the gnome-launcher, you should use this launch command:
wine "/path/to/war3/Frozen Throne.exe" -opengl
or
wine "C:\path\to\war3\Frozen Throne.exe" -opengl

Warcraft 3 runs absolutely great through wine indeed :D

---

### Post by fermulator on 2009-05-11
That's the kicker though.

I have a war3.sh script (which does already have the
```
WINE war3.exe -opengl &
```
command in it.

So:
 Open Terminal -- ~/scripts/war3.sh --- works
 gnome app launcher -- ~/scripts/war3.sh --- doesn't work.

It's the same script being executed either way, but when the script is run from the gnome-application launcher method .. it doesn't work at all!

---

### Post by bhaverkamp on 2011-02-15
> **fermulator said:**
> That's the kicker though.

I have a war3.sh script (which does already have the
```
WINE war3.exe -opengl &
```
command in it.

So:
 Open Terminal -- ~/scripts/war3.sh --- works
 gnome app launcher -- ~/scripts/war3.sh --- doesn't work.

It's the same script being executed either way, but when the script is run from the gnome-application launcher method .. it doesn't work at all!

I am having the same issue. Did you ever find a solution?

---

