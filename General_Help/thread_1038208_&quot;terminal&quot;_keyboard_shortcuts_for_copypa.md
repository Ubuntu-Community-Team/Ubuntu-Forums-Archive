---
title: "&quot;terminal&quot; keyboard shortcuts for copy/paste reset"
date: 2009-01-12
forum: General Help
---

### Post by michael_1234 on 2009-01-12
This is only a minor inconvenience, but if someone knows the answer I'd be appreciative (and a bit surprised).

The Question: in gnome-terminal, is it possible disable resetting keyboard shortcuts directly in-place in the menu, so that keyboard shortcuts can ONLY be changed/reset under the "keyboard shortcuts..." user-interface?

Background: I don't use the mouse for very much, especially when in "terminal" (/usr/bin/gnome-terminal).  I always use the keyboard shortcuts to copy/paste (shift-control-C, shift-control-V).  I use "Alt" + arrows + keyboard to activate menu items like "File.." and "Edit..."

The Problem: all-too-often I'm typing away and accidentally change the keyboard shortcut for "paste" (doesn't happen that often for "copy").  It may be changed, for instance, to the letter "p".  So, whenever i type "p" I paste the contents of the clipboard to terminal!

To reproduce: just activate the menu "Edit" in gnome-terminal, and if you type ANYTHING while the "paste" menu is highlighted, you get a new keyboard shortcut for paste...!!!  (You can also set/reset keyboard shortcuts through the "normal" short-cut editor, "Edit"->"Keyboard shortcuts...".   That's that *only* place I'd like to have these be able to be updated.)


Hope that makes sense,
-michael

---

### Post by mcduck on 2009-01-12
Go to System/Preferences/Appearance, and on the Interface-tab make sure "Editable menu shortcut keys" is disabled.

---

### Post by michael_1234 on 2009-01-12
That did it!  

Thanks,
-m

---

