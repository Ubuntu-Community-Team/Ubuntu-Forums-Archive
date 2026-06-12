---
title: "gnome-terminal &quot;Use background settings from system theme&quot; (changing GTK theme?)"
date: 2011-01-17
forum: Desktop Environments
---

### Post by fermulator on 2011-01-17
I'd like to change the default transparency level for the gnome-terminal.

The gnome-terminal has this setting in: Edit --> Profile preferences --> Background tab, called "Use background settings from system theme".  Indeed, I can simply uncheck this setting and manually adjust, but then my changes would apply to all themes, if I were to change my theme in the future.

How can I edit the transparency of the GTK theme itself so that it applies to gnome-terminal?

I'm running Ubuntu 10.10 with the "Ambiance" theme, and I'm seeing these files which are probably relevant:
> /usr/share/themes/Ambiance/gtk-2.0/gtkrc
/usr/share/themes/Ambiance/gtk-2.0/apps/gnome-terminal.rc

Am I on the right track? (those files don't contain anything obvious like "transparency" or "opacity" to change ... so I"m not exactly sure what/where to change)

---

### Post by Krytarik on 2011-01-17
I've most recently found out how to use and adjust transparency on the desktop, I had not much interest in that feature until I saw some amazing screenshot with it enabled.

Since it is a Compiz feature, go to "System -> Preferences -> CompizConfig Settings Manager -> Accessibility -> Opacity...", in the list that shows up then, you can set up your desired rules for windows. For gnome-terminal the rule would be like this:
```
class=Gnome-terminal & type=Normal
```then you can choose your desired opacity level, 0 = invisible, 100 = intransparent.

If you click at "Grab" in the "New" dialog, you can find the values of another windows you might want to set up, here is a guide for those rules:
[http://wiki.compiz.org/WindowMatching](http://wiki.compiz.org/WindowMatching)

Greetings. Enjoy.:P

EDIT: Oh, I just yet re-read your post, and what I described is exactly what you not want. However having some experience with GTK-themes in the last days, I'm pretty sure that transparency is not set by theme itself.

---

### Post by Frogs Hair on 2011-01-17
You can go to Terminal > Edit > Profile Preferences > Color > Use color from system theme . As said no transparency will be applied unless included with the theme .

---

### Post by Adam's AI on 2011-06-09
You were close; I looked this up while trying to do something similar, and I think you need to go to

```
/usr/share/themes/Ambiance/gtk-2.0/apps/gnome-terminal.rc
```There, you can modify the value on the line:
```
TerminalScreen::background-darkness = 0.95
```Hope that helps!

---

