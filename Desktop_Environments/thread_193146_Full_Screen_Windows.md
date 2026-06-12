---
title: "Full Screen Windows?"
date: 2006-06-09
forum: Desktop Environments
---

### Post by xmiller on 2006-06-09
In KDE, the window menu (or whatever the widget was called on the upper left corner of each window), had the option to put the window in full screen mode (something like Advanced > Fullscreen). To get out of it one could alt-F4 to close it or alt-F3 to bring upthe window menu and minimize/restore, etc. I can't figure out how to get this functionality within Gnome.

In this particular situation, I'm working with xvncviewer windows. I realize I can use vnc's full screen mode and it's good for the initial connection, but it's pretty wonky if I have to drop in and out of full screen mode or want to switch to another task without closing the vnc connection.

---

### Post by popkid on 2006-06-14
[QUOTE=xmiller]In KDE, the window menu (or whatever the widget was called on the upper left corner of each window), had the option to put the window in full screen mode (something like Advanced > Fullscreen). To get out of it one could alt-F4 to close it or alt-F3 to bring upthe window menu and minimize/restore, etc. I can't figure out how to get this functionality within Gnome.

In this particular situation, I'm working with xvncviewer windows. I realize I can use vnc's full screen mode and it's good for the initial connection, but it's pretty wonky if I have to drop in and out of full screen mode or want to switch to another task without closing the vnc connection.[/QUOTE]

I have found a solution to this as I had the same problem...

in a terminal window enter:

gconf-editor

then in gconf editor you can set a keybinding to toggle fullscreen

under apps>metacity>window_keybindings>toggle_fullscreen

edit the entry for this from disabled to the keys to type in to toggle, i.e, I have set

<ctrl><alt>f

this will toggle any window in gnome to and from fullscreen 

in my case this also covers the gnome top panel, which fullscreen in vnc did not....

hope this helps you,

pK

---

### Post by LineOf7s on 2006-11-29
Sorry to dredge up an old thread, but it's the most relevant I've found to ask in:

Toggling to and from fullscreen mode is all well and good (you can also set this in System -> Preferences -> Keyboard Shortcuts), but is it at all possible to somehow set fullscreen mode as a default for a particular application (specifically I'm thinking gnome-terminal)?  

I've got it set currently to 'fill the screen', but it's not fullscreen mode, and it seems a bit odd to have to toggle to it manually each time.

Any clues?

---

