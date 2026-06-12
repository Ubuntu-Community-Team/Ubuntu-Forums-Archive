---
title: "hardcoded keyboard shortcut in gnome?"
date: 2007-12-21
forum: Desktop Environments
---

### Post by moon_goose on 2007-12-21
Hi,

Is there a way to change a shortcut for switching between workspaces in gnome?
(yes, I did look into System->Preferences->Keyboard Shortcuts)

TIA

---

### Post by Tenken on 2007-12-21
If you are running compiz you can use can set key bindings in CompizConfig Settings Manager. Without Compiz you can use the System->Preferences->Keyboard shortcuts, they're near the bottom under Window Management, they are disabled by default, just click on them and in the right column should it should say "New Accelerator" then all you need to do is click the key combo you want to switch workspaces with.

---

### Post by moon_goose on 2007-12-22
Tenken, thank you for replying

Problem was that (I am always doing _by default_ not many people would even consider :) - Workspace Switcher removes its entries from the Preferences if number of workspaces equals 1, but doesn't disable actual bindings (I guess it is Gnome's responsibility?), so binding stays, but without a chance to change it.

---

