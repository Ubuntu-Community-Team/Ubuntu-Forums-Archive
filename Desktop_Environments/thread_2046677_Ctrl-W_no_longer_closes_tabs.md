---
title: "Ctrl-W no longer closes tabs"
date: 2012-08-23
forum: Desktop Environments
---

### Post by truant on 2012-08-23
I can't pinpoint exactly when this happened, but it was recently.

Ctrl-w no longer closes a tab when the cursor is focussed in that tab.  Eg: in Chrome, I can ctrl-w to close a tab unless the omnibox or a form field on a page has focus.

Same same in Firefox, Gedit, everything I've tried.

Ctrl-w in those circumstances deletes a word.

I've dug around in gsettings and can't see a setting which would help.  Keyboard Shortcuts has nothing.

Any clues?  It's a pita to have to click out of text controls just to close a tab.  Ctrl-w has worked to do that for as long as I can remember, it's really not a key combo which should be nerfed.

[edit - sorry, Ubuntu 12.04, Gnome Shell, up to date as of date of posting ]

---

### Post by truant on 2012-08-23
Doh.

Gnome-tweak-tool --> Theme --> Keybinding theme

Was set to EMACS.  Turned it back to 'default' and all was well.

---

