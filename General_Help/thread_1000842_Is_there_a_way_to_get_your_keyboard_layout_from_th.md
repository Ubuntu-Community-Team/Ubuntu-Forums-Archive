---
title: "Is there a way to get your keyboard layout from the command line?"
date: 2008-12-03
forum: General Help
---

### Post by StevePerkins on 2008-12-03
I'm used to switching back and forth between the standard QWERTY and Dvorak keyboard layouts.  Typically, in Gnome or MS-Windows, I configure <ALT>+<SHIFT> as a hot-key to switch back and forth between those two keyboard layouts.

However, I just started a new job where my workstation runs an older version of Ubuntu with KDE 3.5 for the desktop environment.  KDE 3.5 has a little keyboard switcher system tray applet, but it's not as nice as Gnome's.  You apparently can configure a hot-key to switch from one language to another, but not between different variants (i.e. qwerty to dvorak) within the same U.S. English keyboard layout.  I have to take my hands off the keyboard and switch layout variants by right-clicking on the tray icon... which sounds trivial, but really gets annoying when you're used to doing this hundreds of times each day.

So I wrote a small shell script that will call the 'setxkbmap' command, and am setting up my hotkey through KDE to call that script.  The problem is that I would like to use the same hotkey to toggle back and forth, so I need some way of knowing what the CURRENT layout variant is so I can switch to the other instead.  Setting an environment variable is no good, because that gets lost when the script finishes and its shell terminates.  

What would be ideal is having some command I could call from the script that could determine what the current layout and variant used by xkb is.  Documentation for xkb is pretty sparse... does anyone know of such a method to tell from the command line what is your current keyboard layout and variant?  Thanks!

---

### Post by gilgongo on 2008-12-14
Bump. Did you find an answer to this? I'd like to know too.

---

### Post by StevePerkins on 2008-12-15
No, I didn't.  However, if it ends up being helpful to your situation, I did end up finding a better solution to my problem.  I modified the keyboard section of my "/etc/X11/xorg.conf" to look like this:

```
Section "InputDevice"
     Identifier   "Keyboard0"
     Driver       "kdb"
     Option       "XkbModel" "pc105"
     Option       "XkbLayout" "us,dvork"
     Option       "XkbOptions" "grp:alt_shift_toggle"
EndSection
```

Just use a comma-separated list of keyboard layouts with the "XkbLayout" option, and set an "XkbOptions" option for alt+shift to be the toggle.  Now, my keyboard layout management happens at the base X-windows level rather than up in the Gnome/KDE/etc level.  To me this is a lot easier and more consistent than bothering with all the separate tool-tray utilities that the various desktop environments use for layout toggling.

---

