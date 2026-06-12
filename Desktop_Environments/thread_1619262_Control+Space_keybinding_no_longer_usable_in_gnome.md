---
title: "Control+Space keybinding no longer usable in gnome"
date: 2010-11-11
forum: Desktop Environments
---

### Post by tomdz on 2010-11-11
I tried to bind a command to Control+Alt+Space in the gconf-editor (/apps/metacity/global_keybindings -> run_command_1), but found that that didn't trigger the app, so I changed the keybinding to Super+r (super being mapped to the windows key).

However, now Control+Space doesn't work anymore which is really annoying since it is the default keybinding for auto complete in a bunch of tools. If I try to re-assign the auto complete in any of these tools, then Control+Space can never be selected. It feels like Gnome or some other tool intercepts the keybinding, though I can't find it anywhere in the gnome config

Is there any way to find out which program captures the keybinding ?

The environment is a mostly default Ubuntu 10.10.

---

### Post by mcduck on 2010-11-11
If you use Metacity as your window manager (no visual effects) then you are looking at the right place already.

If you use Compiz (visual effects enabled) then install CompizConfig Settings Manager and check the shortcuts there.

---

### Post by tomdz on 2010-11-11
I did that, for both metacity and compiz, and couldn't find any setting for Control+Space.

Tom

---

