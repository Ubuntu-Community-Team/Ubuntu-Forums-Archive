---
title: "Help me with my .xinitrc - login problems"
date: 2009-01-08
forum: Desktop Environments
---

### Post by Hooya on 2009-01-08
I'm attempting to use the sample ~/.xinitrc from here
[http://www.rapierbit.org/linux/winmgrs.html](http://www.rapierbit.org/linux/winmgrs.html)
to try and make it easier to log into to multiple desktop environments/window managers via ctrl+alt+F1, F2, etc.

My default install is Gnome (Ubuntu) but I primarily go straight to Fluxbox and also have KDE installed.  I can get all three running in separate virtual terminals, but I need to manually edit above said text file, go to my tty2, "$startx -- :2" to get a different window manager other than Gnome running.

So my steps:
1. Start up.  Automatically logs into Fluxbox.
2. ctrl+alt+F1, run "$startx -- :1" and I get a Gnome session in ctrl+alt+F9
3. echo "exec startkde" to the ~/.xinitrc file
4. ctrl+alt+F2, run "$startx -- :2" and I get a KDE session in ctrl+alt+F10

I want to be able to, from the terminal, without step 3 above, to enter the commands:
$startx kde -- :2
$startx gnome -- :1
to get those environments in those sessions.  Without editing that text file.

Using the ~/.xinitrc from the site linked above I get errors related to FreeFontPath.  Any idea what I need to do?  I cannot get gdm to run, as it always reports that a login manager is already running

---

### Post by Hooya on 2009-01-09
OK, well I figured out that for whatever reason, all of this is totally unnecessary, and I also figured out why the sample xinitrc wasn't working.

The command I was looking for is simply this:

$startx /usr/bin/startkde -- :2

I don't know why you need the "/usr/bin/" in the argument, but you do.  Now I start my gnome session like:
$startx -- :1
and my KDE session like above.  All is right with the world.

No .xinitrc needed at all.

---

