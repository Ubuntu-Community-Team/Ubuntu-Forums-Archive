---
title: "Neither Alt key works"
date: 2009-10-28
forum: Desktop Environments
---

### Post by Rakshasa on 2009-10-28
When I hold down either Alt key, it has no effect on the keystroke, e.g. Ctrl-Alt-F is the same as pressing Ctrl-F, Alt-Tab doesn't work, I can't use many Compiz commands, etc.  However, I used some console command a while back (think it was "xev") and found that my Alt keys are recognized as ISO_Level3_Shift, and when trying to set a shortcut in the Compiz settings manager or in the Keyboard Shortcuts dialog my left Alt key is recognized as Mod5.  Keyboard shortcuts using Mod5 work, but I'm looking for a cleaner solution than manually changing all my keyboard shortcuts.  Does anyone know how I could map the Mod5 event to my Alt keys?

EDIT: Now, in the Keyboard Shortcuts dialog, a keystroke like Alt+X is recognized as Alt+Mod5+X :S

---

### Post by Rakshasa on 2009-10-28
I managed to resolve the problem by running "xmodmap /usr/share/xmodmap/xmodmap.us-ibm" and restarting the X server.

---

