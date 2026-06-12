---
title: "Window tiling and resizing in Ubuntu MATE?"
date: 2015-06-14
forum: Desktop Environments
---

### Post by vasa1 on 2015-06-14
How does Ubuntu MATE 1**4**.04 compare with DEs such as Lubuntu 14.04 or Xubuntu 14.04 in how configurable window tiling and resizing are? Does it have keyboard shortcuts like Openbox has? Can users set up their own keyboard shortcuts to resize (and reposition) a window?

---

### Post by tgalati4 on 2015-06-14
I'm running MATE 1.8 (Linux Mint version) based on 14.04.  Alt-F8 will resize the active window.  There are several shortcuts available to maximize, minimize, and switch windows.  Many windows-manipulation shortcuts are not assigned by default, but you can assign them.  For window positions, they will open where your cursor is or in the center--depending on your Windows Preferences.  Windows snapping is supported with side-by-side tiling.  My only recent experience with LXDE is on my RaspberryPi.  There are small differences, but otherwise they behave in a similar fashion.

---

### Post by vasa1 on 2015-06-14
@tgalati4, are these shortcuts keyboard shortcuts and are they available with Marco or Compiz? I can't use Compiz.

But I'll give the live USB another go and look around some more.

Just to give you an example of what I have in Openbox:
Super + down arrow places the active window in the lower half of the screen with full width.
Super + up arrow places the active window in the upper half of the screen with full width.
Super + left arrow places the active window in the left half of the screen with full height.
Super + right arrow places the active window in the right half of the screen with full height.
Super + W just centers the active window but doesn't resize it.
Super + 6, 7, 8, and 9 place the active window at the top left, top right, bottom right, and bottom left corners of the screen.

---

### Post by Dennis N on 2015-06-14
_Ubuntu MATE 14.04_ (with default window manager Marco) can tile windows to the left or right side (but not top or bottom) by dragging. There are no keyboard shortcuts to do this in one step, although I think they are working on it. The closest are move window to left (or right) edge.  Also can move window to the corners via keyboard, and maximize/minimize/restore with keyboard. Lots of keybindings for actions are left undefined. **Grade: B-**

_Xubuntu_: Tile to any edge and restore size, by dragging or keyboard shortcut. Shortcut toggle to maximize/unmaximize in all ways: horiz, vert, both. **Grade: A**.

_Lubuntu_: clearly you already know. From what I remember last time I looked at this, it won't restore window size if tiled. Does that work now? **Grade C**. (But it's lightweight!)

---

### Post by kerry_s on 2015-06-14
> **vasa1 said:**
> @tgalati4, are these shortcuts keyboard shortcuts and are they available with Marco or Compiz? I can't use Compiz.

But I'll give the live USB another go and look around some more.

Just to give you an example of what I have in Openbox:
Super + down arrow places the active window in the lower half of the screen with full width.
Super + up arrow places the active window in the upper half of the screen with full width.
Super + left arrow places the active window in the left half of the screen with full height.
Super + right arrow places the active window in the right half of the screen with full height.
Super + W just centers the active window but doesn't resize it.
Super + 6, 7, 8, and 9 place the active window at the top left, top right, bottom right, and bottom left corners of the screen.


i only see the basics in keyboard shortcuts.

---

### Post by tgalati4 on 2015-06-14
There are additional settings in Windows Preferences in Menu-->Application--> Preferences.  But yes, MATE has basic window management.  There may be some additional tools that you can install, but I am not familiar with them.  I recall bluetile and devilspie among others.

---

### Post by Dennis N on 2015-06-15
> **tgalati4 said:**
> There are additional settings in Windows Preferences in Menu-->Application--> Preferences.  But yes, MATE has basic window management.  There may be some additional tools that you can install, but I am not familiar with them.  I recall bluetile and devilspie among others.

Keyboard shortcuts for Ubuntu MATE related to windows actions are set up in either **Keyboard Shortcuts > Window management section** or the **dconf-editor** tool. For example, if you want a keyboard shortcut to center a window on the screen, or a toggle key to maximize/unmaximize it, look there to define it.

---

### Post by cooleryawner on 2015-06-17
Ye, I am pretty sure MATE has keyboard settings for resizing windows, but if your all about tiling maybe a titling window manager like i3.

---

