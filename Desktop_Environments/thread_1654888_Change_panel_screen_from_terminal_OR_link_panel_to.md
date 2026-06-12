---
title: "Change panel screen from terminal OR link panel to display not screen"
date: 2010-12-29
forum: Desktop Environments
---

### Post by SnickerSnack on 2010-12-29
I have a laptop that I use with a second display from time to time (both at work and at home), and I need some more flexibility with the xfce panel.

When I'm at home, I have the second monitor (VGA1 henceforth) physically on the left-hand-side, but I want the panel on the main laptop screen (LVDS1 henceforth), which is on the right.  Of course I can do this by opening the panel properties and setting "Select Monitor" to "2".  However, when I turn off VGA1, I have no panel, since that was screen 2.  Thus, I'd have to change the panel from 1 to 2, and then back again.....every time.

I have some xrandr commands set in some buttons on the panel so that it's easy to switch the screens around quickly.  I use some rotation scripts (it's a tablet) and I've been using

xrandr --output VGA1 --mode 1024x768 --same-as LVDS1
xrandr --output VGA1 --off
xrandr --output VGA1 --right-of LVDS1 --mode 1280x1024
xrandr --output VGA1 --right-of LVDS1 --mode 1024x768

though this puts the left-hand screen on the "right" (that is, as far as display topology).

I'd either like to tie the panel to LVDS1 or be able to change the screen that the panel is on (from 1 to 2, and back) from the command line so that the buttons I have set up can do it for me.

I've looked around on google and thinkwiki.org, but I didn't find anything.  I've tried setting the panel to screen 2 with "Span Monitors", but that's really not ideal.

EDIT: I've tried using this:

```
zsharon@Weierstrass:~$ xfce4-panel --help-all
Usage:
  xfce4-panel [OPTION...] 

Help Options:
  -h, --help               Show help options
  --help-all               Show all help options
  --help-gtk               Show GTK+ Options

GTK+ Options
  --class=CLASS            Program class as used by the window manager
  --name=NAME              Program name as used by the window manager
  --screen=SCREEN          X screen to use
  --sync                   Make X calls synchronous
  --gtk-module=MODULES     Load additional GTK+ modules
  --g-fatal-warnings       Make all warnings fatal

Application Options:
  -V, --version            Print version information and exit
  -c, --customize          Show 'Customize Panel' dialog
  -s, --save               Save the panel configuration
  -r, --restart            Restart the running instance of xfce4-panel
  -q, --quit               Log out the active session
  -x, --exit               Close all panels and end the program
  -a, --add                Show 'Add New Items' dialog
  --display=DISPLAY        X display to use

```

But displays can't be opened:

zsharon@Weierstrass:~$ xfce4-panel --display=1
xfce4-panel: Cannot open display: 1

and

zsharon@Weierstrass:~$ xfce4-panel --screen=X

apparently has the same result for any X.  Huh?

---

