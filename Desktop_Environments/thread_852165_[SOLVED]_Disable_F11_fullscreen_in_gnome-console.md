---
title: "[SOLVED] Disable F11 fullscreen in gnome-console?"
date: 2008-07-07
forum: Desktop Environments
---

### Post by Beanalby on 2008-07-07
I'm using gnome-console in Ubuntu 8.04, and pressing F11 makes the console fullscreen.  I'd like the key to be sent to the console instead, any ideas how to configure this?

Preferences -> Keyboard Shortcuts didn't list anything as being assigned to "toggle fullscreen mode", and assigning it a new shortcut (such as Alt+Enter) makes that a fullscreen shortcut in addition to F11.

I've already disabled all global keyboard shortcuts in gnome-console, and this successfully makes things like Ctrl-p go to the console instead of doing a shortcut, but I can't find anything else for F11.

---

### Post by 01mf02 on 2008-07-07
You probably use 3D desktop effects, which control this aspect of window management. To change what happens when you press F11, you have to install the "Advanced Desktop Effects Settings" program and configure it there - note however that this can be a quite complicated task!

Good luck!

---

### Post by Car60n on 2008-07-07
try doing this--
1>open terminal and type this
```
gconf-editor
```
2>when the configuration editor opens press ctrl-f or edit-find
3>type this in the find box
/apps/gnome-terminal/keybindings/full_screen
4>edit the fullscreen key to whatever...

that should do it..

---

### Post by Beanalby on 2008-07-08
> **Car60n said:**
> try doing this--
1>open terminal and type this
```
gconf-editor
```
2>when the configuration editor opens press ctrl-f or edit-find
3>type this in the find box
/apps/gnome-terminal/keybindings/full_screen
4>edit the fullscreen key to whatever...

that should do it..


That was it exactly - it was set to "F11", changed it to "disabled"; now I can still use the "keyboard shortcut" setting of Alt-Enter to get fullscreen and F11 properly goes to the terminal.

Thanks!

---

### Post by zippy51 on 2013-01-04
> **Car60n said:**
> try doing this--
1>open terminal and type this
```
gconf-editor
```
2>when the configuration editor opens press ctrl-f or edit-find
3>type this in the find box
/apps/gnome-terminal/keybindings/full_screen
4>edit the fullscreen key to whatever...

that should do it..

Thank you for this answer as well.  I am running the Turnkey-MVS system under the Hercules (IBM mainframe) emulator under Ubuntu 12.04.  F11 is intended to be processed as an MVS command by my telnet session but, instead, was being intercepted by gnome, throwing my telnet xterm into fullscreen mode.  Your recommendation fixed my problem.  I changed the fullscreen key to F2 and the F11 key press now gets passed to MVS and does what it is supposed to do.  I appreciate the help.

---

### Post by SantaFe on 2013-01-05
> **zippy51 said:**
> Thank you for this answer as well.  I am running the Turnkey-MVS system under the Hercules (IBM mainframe) emulator under Ubuntu 12.04.  F11 is intended to be processed as an MVS command by my telnet session but, instead, was being intercepted by gnome, throwing my telnet xterm into fullscreen mode.  Your recommendation fixed my problem.  I changed the fullscreen key to F2 and the F11 key press now gets passed to MVS and does what it is supposed to do.  I appreciate the help.This post's so old, Father Time himself has paid a visit to it! ;)

:lolflag:

---

