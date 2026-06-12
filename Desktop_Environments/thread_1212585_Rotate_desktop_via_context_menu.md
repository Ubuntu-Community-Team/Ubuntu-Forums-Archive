---
title: "Rotate desktop via context menu"
date: 2009-07-13
forum: Desktop Environments
---

### Post by Kralizec on 2009-07-13
Hello,

I've extensively searched for this and come up with very little to no results. What I'm aiming for is a way to have, in the right-click context menu for the desktop, an option to rotate my desktop to the right, or to the left. I am using the Compiz cube, if this helps with any responses. I've looked for a way to control the cube via terminal, with no luck.

The only thing I've seen that was a possible solution was to create scripts that would simulate the hotkey keystrokes to rotate left and right, respectively, and add them to the file/folder right click context using Nautilus Actions. This worked sort of: it would rapidly rotate my cube, going far past the desktop I wanted, even when I had it immediately deactivate the keystroke:
```
xsendkeycode 114 1
xsendkeycode 114 0
```
This also strangely affected my screen resolution to the point where I had to restart X.
If anyone has any other insight into this, I'd be very glad to hear it.

---

