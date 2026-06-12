---
title: "Can't drag windows since upgrade"
date: 2011-05-03
forum: Desktop Environments
---

### Post by PantsManUK on 2011-05-03
Since upgrading from Maverick to Natty (and re-enabling Desktop Cube/Cube Rotation in Compiz) I am unable to drag windows any more.

Did a quick search and found nothing, so I'm guessing this is (currently) a unique problem, but any assistance in fixing would be appreciated.

*Update*: And I'm sure this'll be diagnostically useful; if I use the window context menu/drop-down and select Move, that also does nothing. Also, the window resize hovers do nothing, but the double-click full size|restore/middle and right click the maximize gadget to horizontally|vertically maximize do work. Further, the window management shortcuts to move windows do nothing.

*Further update*: and if I turn off Desktop Cube/Cube Rotation and go back to Wall/Expo, I still can't move windows using any of the methods mentioned in my previous update.

---

### Post by PantsManUK on 2011-05-04
This is just another update, but since it's a new day I think a new post is warranted.

I can confirm that the problem is with my local installation only; I made a "from scratch" installation in VirtualBox and window dragging works just fine in Unity on that.

So, other than the "nuke from orbit"/Microsoft approach (format and re-install), does anyone out there have any suggestions for what I can do to get dragging working again?

---

### Post by Krytarik on 2011-05-04
Make sure that the plugins "Move Windows" and "Resize Windows" are enabled in "CompizConfig Settings Manager -> Window Management".

Greetings.

---

### Post by PantsManUK on 2011-05-04
Krytarik,

Thanks for that, I feel like such a fool now :oops:

That's all it was, Move and Resize Windows must have turned themselves off back when I first re-enabled Cube/Rotate.

---

### Post by Krytarik on 2011-05-04
> **PantsManUK said:**
> 
Move and Resize Windows must have turned themselves off.
Most probably during the process of re-enabling the Cube.

You're welcome!

---

