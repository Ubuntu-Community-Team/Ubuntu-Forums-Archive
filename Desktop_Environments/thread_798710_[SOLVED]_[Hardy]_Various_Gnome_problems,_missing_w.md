---
title: "[SOLVED] [Hardy] Various Gnome problems, missing window decorations"
date: 2008-05-18
forum: Desktop Environments
---

### Post by rrwo on 2008-05-18
I've installd Gnome on a relatively-fresh install of XUbuntu Hardy.  There are two noticable problems:

1. When the user first logs into a Gnome session, one gets error message "The panel encountered a problem while loading 'OAFID:GNOME_FastUserSwitchApplet'" with the Don't Delete/Delete option.

This has nothing to do with restarting X. It happens every time, even from a fresh boot of the system.

UPDATE: this issue ws fixed by installing the Fast User Switching Applet: I guess the default profile uses it, but it's not a dependency.

2. The other is more serious: all windows open in the top-left corner, and have no window decorations.  The window switcher doesn't work nor can windows be resized or moved.

It's a ThinkPad with an Intel video card, not an ATI of NVidia card, where this is a known issue.  The workaround for adding "AddARGBVisuals" options to xorg.conf doesn't work.

I've tried editing Emerald themes or even removing emerald. Doesn't work either.

3. There's only one workspace, not the default two. I don't get an option to add workspaces.

4. When I go to Settings -> Preferences -> Windows, I get a "Cannot start the prferences applicastion for your window manager. Window manager 'unknown' has not registered a configuration tool" error.

UPDATE: I've uninstalled Compiz, and the window doecorations are still missing. So I don't think it's a compiz problem at all.

I note that Xfce works fine on that machine.

UPDATE: This remaining issues were fixed by installing metacity. Apparently it's not a dependency for installing Gnome.

---

