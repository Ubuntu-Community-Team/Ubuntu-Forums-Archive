---
title: "How multiple windows works and how it should work"
date: 2011-05-12
forum: Desktop Environments
---

### Post by cragwolf on 2011-05-12
Let's say you have two Nautilus windows, A and B, open. If:

1) both windows are minimised: clicking once on the Nautilus launcher button will un-minimise both windows. Click the button again will send the windows into scale mode. If you now select window B, then window A will remain un-minimised. So 3 clicks to get window B for sure (after all, window B could have been hidden under window A), and the original minimisation state of window A is not remembered.

2) window A is minimised, window B is un-minimised: click once on the Nautilus launcher immediately sends you to the scale mode. If you now select window B, window A is minimised again. So this time, 2 clicks to get window B, and the original minimisation state of window A is remembered.

This behaviour is inconsistent, inefficient and dumb.

This is how it should work for when you have more than one window:

No matter what the initial minimisation state of the windows, one click on the Launcher button sends you straight to the scale mode, and now when you select a window, the minimisation states of the other windows are remembered. So you never have to click more than twice to access a window, and you don't get a mess of windows showing up when you just want to work on one.

Tips and criticisms are welcome.

---

### Post by gabrielaca on 2011-05-12
either that or get two thumbpreviews on the launcher and click just once

---

### Post by mc4man on 2011-05-12
> This behaviour is inconsistent, inefficient and dumb.
Don't consider it any of those - the scale function of launcher icon is where it was able to get during the dev. (and it did change a bit

There are actually several more scenarios than you've listed and in that regard I'd term it a bit confusing.(though completely consistent per scenarios

In fact here minimized windows will be returned to a min state if not picked depending on their location relative to where (what ws), you initiate the window group picker and what focus is on when doing so

It wouldn't surprise me if the l. click on icon was adjusted in 11.10, though here am fairly happy with the current state

---

