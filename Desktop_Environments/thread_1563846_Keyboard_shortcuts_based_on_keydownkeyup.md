---
title: "Keyboard shortcuts based on keydown/keyup"
date: 2010-08-29
forum: Desktop Environments
---

### Post by Yudley on 2010-08-29
I frequently come across scenarios in which i have to switch b/w two windows frequently, e.g.:

- I have firefox and my editor open ... i need to keep typing something in the editor but scroll down a firefox page from time to time
- I have a video running and slides (images) open in parallel ... i need to keep flipping the slides while the video plays ... but sometimes i need to pause the video for a few seconds

in these scenarios i mainly want my keyboard focus on one app but occasionaly do something on another app ... but the procedure for doing that is cumbersome ... e.g., i have to Alt+Tab then PgDn or PgUp and then Alt+Tab again

is it possible to assign key-down or key-up events to Alt+Tab behavior? so that i press Ctrl (or Mod key) and it switches focus to the other window and while the key is pressed i do a PgDn or PgUp and that applies to the new window ... and when i release the Ctrl key the focus is back to the first window

that is, instead of doing this:

Alt+Tab, PgDn, Alt+Tab

I do something like:

Ctrl+PgDn

i guess this issue is part of a general problem of fine-grained control of keyboard shortcuts ... e.g., in System->Preferences->Keyboard-Shortcuts (in Gnome) for each shortcut there should be a provision to specify whether the action should be taken on KeyPress or either of KeyDn or KeyUp

---

