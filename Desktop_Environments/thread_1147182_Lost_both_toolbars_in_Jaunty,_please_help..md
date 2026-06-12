---
title: "Lost both toolbars in Jaunty, please help."
date: 2009-05-03
forum: Desktop Environments
---

### Post by omgpop on 2009-05-03
After customizing the toolbars a little more to my personal preference, I tested it out by clicking the shut down button which I had put on one of the toolbars. When I booted it back up, the toolbars were gone. See, without them I can't really do much of anything with this things, so help would be much appreciated.

---

### Post by drs305 on 2009-05-03
Try ALT-F2 and (assuming gnome):
```
gnome-panel
```
and see what, if anything, is recovered from your efforts.

---

### Post by omgpop on 2009-05-03
For some reason (and I have tried before when searching help topics) alt+f2 doesnt do anything.

---

### Post by omgpop on 2009-05-03
Any other suggestions?

---

### Post by drs305 on 2009-05-03
> **omgpop said:**
> For some reason (and I have tried before when searching help topics) alt+f2 doesnt do anything.

Not to get sidetracked (but it *is* your thread), have you checked gconf to see what key binding is assigned to the run dialog and/or ALT-F2. Added: See how to open Terminal below.
```

gconf-editor /apps/metacity/global_keybindings/panel_run_dialog

```

As far as the panels go, what happened when you tried running "gnome-panel" from a terminal?  (Applications, Accessories, Terminal)

---

### Post by pauna on 2009-05-03
> **omgpop said:**
> Any other suggestions?

If you have a completely empty desktop (no panels or anything), but you can still right click with your mouse, you can from the right-click menu select "Create launcher".

In the launcher creation dialog, choose "application" and use the command "gnome-terminal". That should create a terminal icon to your desktop and from there you can launch back the gnome-panel as instructed previously.

---

### Post by omgpop on 2009-05-03
Right, see now I'm new so this is excusable I think, but that peice of text in a box with the forward slashes, is that a file location? If it is okay, but if not, well I can't get into terminal by any means I know of since my toolbars are gone. What is gconf-I imagine gnome configuration, but how can I get to it?

---

### Post by omgpop on 2009-05-03
Oh, how embarrassing, pauna thank you very much, that worked. Thank you to everyone else who helped too.

---

### Post by dazzlindonna on 2009-05-03
Try pressing Ctrl-Alt-T .  That's the keyboard shortcut that works for me to open up terminal and I assume it's the default shortcut, since I don't recall ever creating it myself.

---

### Post by drs305 on 2009-05-03
> **omgpop said:**
> Right, see now I'm new so this is excusable I think, but that peice of text in a box with the forward slashes, is that a file location? If it is okay, but if not, well I can't get into terminal by any means I know of since my toolbars are gone. What is gconf-I imagine gnome configuration, but how can I get to it?

Forgot you didn't have *any* menus. But that code was a command to open up gconf-editor. It lets you look at various settings for many things that gnome runs: icon sizes, key bindings (like ALT-F2), whether or not you see the Desktop and volumes (partitions), etc. 

You may see helpers give commands that start with "gconftool-2" and then a string such as the one I gave you. These commands will change the settings automatically without you having to open gconf-editor itself.

Many of the settings for what you see are also available through nautilus file browser's preferences menus.

One more thing as a practical example. Once you get your panels the way you like them, you can save the setting so you can restore it should they be lost or altered. The command to save them (to a Desktop file but you can change the location/name) is:
```
gconftool-2 --dump /apps/panel > ~/Desktop/panel_settings
```

To restore a saved panel:
```
gconftool-2 --load ~/Desktop/panel_settings && killall gnome-panel
```
Note: the second half of the command merely refreshes the Desktop.

---

