---
title: "Lucid How to change Gnome / Nautilus keyboard shortcuts"
date: 2010-05-05
forum: Desktop Environments
---

### Post by AnotherMuggle on 2010-05-05
Karmic there was a tab inside "System->Preferences->Appearance" called "Interface" which allowed me to modify the keyboard shortcuts.  I had <Backspace> to move backwards in Nautilis and <Shift><Backspace> to move forward.

Without this tab can anyone tell me how I can modify the shortcuts to do this?

I have spent some time looking at gconf-editor but nothing is jumping out at me, particularly with regards to the back and forward browsing.

Cheers,
Tom

---

### Post by Bobhuber on 2010-05-05
> **tomkear2006 said:**
> Karmic there was a tab inside "System->Preferences->Appearance" called "Interface" which allowed me to modify the keyboard shortcuts.  I had <Backspace> to move backwards in Nautilis and <Shift><Backspace> to move forward.

Without this tab can anyone tell me how I can modify the shortcuts to do this?

I have spent some time looking at gconf-editor but nothing is jumping out at me, particularly with regards to the back and forward browsing.

Cheers,
Tom
System-Preferences-Keyboard Shortcuts is I think what you are looking for.

---

### Post by AnotherMuggle on 2010-05-05
> **Bobhuber said:**
> System-Preferences-Keyboard Shortcuts is I think what you are looking for.

Yea I had looked at that but I'm not convinced they are the right "kind" of shortcuts.  They don't appear to include the back and forward buttons and look more like buttons for things such as turning volume and screen brightness up and down.

Unless I am missing something here?

---

### Post by AnotherMuggle on 2010-05-06
I figured this one out for myself with lots of trial and error :)

For the benefit of anyone else facing the same issue:

In gconf-editor tick the key:
/desktop/gnome/interface/can_change_accels

This turns on the editable menus.  Hover over a menu item and press the new keyboard shortcut to assign it.  Then untick the above item again in gconf-editor so that you don't accidentally change any more menu shortcuts.

---

### Post by ahannigan on 2010-05-27
Thanks Tom, I'd nearly given up finding it!

Aidan

---

