---
title: "Some windows shortcuts"
date: 2007-09-23
forum: Desktop Environments
---

### Post by s-lime on 2007-09-23
How can I make these 2 shortcuts work on ubuntu 7.04:

ALT+TAB: Swith between applications/desktops

CTRL+ALT+DELETE: Move system manager to top, pausing all other applications.

Thanks for your time.

---

### Post by jrib on 2007-09-23
alt-tab should already be cycling through applications.  I'm not sure how to make it cycle applications on all workspaces.

Pausing all other applications would probably take some scripting and I don't know that it would work so well.

If a keyboard shortcut is not listed in the menu (System -> Preferences -> Keyboard Shortcuts), then you can create a custom one using gconf-editor.

In gconf-editor, you create the command you want in one of the keys at /apps/metacity/keybinding_commands and then you set the corresponding keys for the command at /apps/metacity/global_keybindings

---

### Post by s-lime on 2007-09-24
Yes, but control alt delete only runs system inspector, but it does not bring it to front, because if I play full-screen 3D game, that doesn't work.

---

