---
title: "How to Disable Keyboard&gt;Mouse Shortcuts"
date: 2010-11-12
forum: Desktop Environments
---

### Post by -tr on 2010-11-12
Hello there. I've been playing WoW on my Ubuntu installation, but I'm having a bit of a trouble using certain keybinds. When holding down alt and pressing one of the mouse buttons, a shortcut button of some form is enabled and negates the keybind; ie: Alt + Right mouse button shows a grabbing hand, Alt + Middle Mouse button shows a diagonal arrow in a corner, and Alt + Left mouse button shows the context menu. 

Surely this is something simple I've missed, but I didn't see anywhere to disable these in either keyboard shortcuts or keyboard / mouse options. Thanks for any help! :)

---

### Post by kem on 2011-04-10
Same problem here. I need to disable Alt + mouse button shortcut because of conflict with OpenOffice Draw. I cannot find it in System -> Preferences -> Keyboard shortcuts.

---

### Post by Krytarik on 2011-04-10
You can set another key as the modifier, but apparently you can't disable those feature completely:
- press Alt+F2
- enter "gconf-editor"
- browse to "/apps/metacity/general/mouse_button_modifier"
- set a key that doesn't get into your way, valid options are (at least):

[LIST]
[*] <Alt>
[*] <Super>
[*] <Control>
[*]<Shift>
[/LIST]
 Greetings.

---

