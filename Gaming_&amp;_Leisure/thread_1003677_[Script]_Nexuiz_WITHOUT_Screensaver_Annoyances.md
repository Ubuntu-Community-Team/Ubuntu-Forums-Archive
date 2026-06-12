---
title: "[Script] Nexuiz WITHOUT Screensaver Annoyances"
date: 2008-12-06
forum: Gaming &amp; Leisure
---

### Post by jenkinbr on 2008-12-06
[size=6][color="DarkRed"]**PlayNex v1.0**[/color][/size]
[size=5]**What is it?**[/size]
PlayNex is a script I've created that will automatically set gconf values to disable gnome-screensaver before starting nexuiz, then re-enables it when the game exits.  This will also work for other games by changing one line of code and saving the script under a new name.

I originally wrote this because I was annoyed with gnome-screensaver's behavior of activating the screensaver 10 minutes into a fragfest, slowing things down, and causing other annoying problems.  After a personal friend came to me wondering about this behavior, I told him what it was and promised him I would get this to him.

Rather than simply e-mailing this tarball to him, I decided that it would be better if I posted it here on UbuntuForums.org for others as well.  


[size=5]**Changelog:**[/size]
PlayNex v1.0: Initial release (current)


[size=5]**INSTALLATION**[/size]
To install this package, simply extract the contents directly into
your home directory.

This package assumes that you installed the nexuiz package from Ubuntu's
Universe repository.  If this is NOT the case, you will need to edit
~/bin/playnex accordingly.

If you did NOT previously have a ~/bin directory, you will either need to add
this to your PATH.  Alternatively, you can logout and login again, and Ubuntu
should automatically add ~/bin to your user PATH.

I have also created a playnex.desktop file, located in ~/.nexuiz/desktop-conf/ 
To use it, simply copy it to your panel or add it to your application menu.
This desktop file also assumes you installed nexuiz from the repositories, as
it references the icon found at /usr/share/pixmaps/nexuiz.xpm

Documentation, license, and other info can be found in the script itself,
located at ~/bin/playnex

After installation, this file can safely be deleted or moved wherever you feel
appropriate.

[SIZE="5"]**What's in the Script?**[/SIZE]
Here is the contents of the script, just in case you are wondering...
```

#!/bin/bash
#
# AUTHOR: <snip> - see the actual file if you want to find out.
# VERSION: PlayNex v 1.0
# LICENSE: GPL v.2+  Feel free to modify and redistribute (or sell, if you
#   really think someone would be stupid enough to buy it :-P)
#
# This script is a handy way of starting the nexuiz game, disableing the
# screensaver before starting, and then re-enabling it when the game exits.
# It was originally created in my lazyness to pause amarok and disable the 
# screensaver before starting nexuiz, but I've stripped the amarok bits
# public release, as not everyone uses this application.
#
# Note that this script is written for those who use the version of nexuiz
# included in the Ubuntu universe repositories, and will need modification
# if you would like to use the official distribution from
# http://www.nexuiz.com/.

# First, disable the screensaver (if it isn't already) (In the future, I would
# like this to detect the setting and store it to a variable before changing
# anything so that the original value can be re-enstated later):
gconftool-2 --type bool --set /apps/gnome-screensaver/idle_activation_enabled 0

# Then, launch Nexuiz.
# Change this line as needed if your nexuiz script/binary is located outside
# your system PATH *or* it has a different name *or* you would like to use
# this for a different game...
nexuiz

# When the game is complete, enable the screensaver before exiting (Future: 
# re-instate value stored in variable from above):
gconftool-2 --type bool --set /apps/gnome-screensaver/idle_activation_enabled 1

# That's It!
exit

```

[size=5]**The Tarball**[/size]
Of course, you can't follow the instrucitons in README.INSTALLATION unless you actually have the file, which is attached below.  If the attachment isn't there, please notify me so I can suitably go play with plasma before fixing it. :)

Happy Nexing :)

---

### Post by lukjad on 2008-12-06
Wow. So it wasn't all talk! You do know something. :shock:

Anyway, good work. ;)

---

### Post by jenkinbr on 2008-12-08
> **lukjad007 said:**
> Wow. So it wasn't all talk! You do know something. :shock:

Anyway, good work. ;)
Shame on you for actually thinking I am stupid... j/k

anyways, I am working on an update that will allow some new things (Thanks to the [Rute User's Tutorial and Exposition]("http://rute.2038bug.com/index.html.gz") for an easy to follow [BASH scripting tutorial]("http://rute.2038bug.com/node10.html.gz")).  Among the planned changes:

[LIST]
[*]Easily change the default command to be run by editing ~/.playnexrc
[*]Command-line specification of the command to be run with the screensaver disabled (e.g. "playnex ~/Nexuiz/nexuiz-linux-glx.sh" and "playnex saurbraten" will now work)
[/LIST]

Expected release date: 2008-12-09
Expected version number: 1.1

---

