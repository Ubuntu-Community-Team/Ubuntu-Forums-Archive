---
title: "Annoying window resizing bug"
date: 2009-05-16
forum: General Help
---

### Post by Bark on 2009-05-16
Since Ubuntu 7, there has been a bug where windows once resized to maximum, then refuse to resize back to their previous size. I've recently installed a completely fresh Ubuntu 8.10 and Ubuntu 9.04 on two different computers, and this bug is still there.

In detail, I resize a partially sized window to maximum using the top right corner button with a square (the one between the underscore and the X), and then I close the window. When I open the same program again, if I try to resize it back to normal using the middle button, it stays at maximum size, but resizeable (ie an arrow appears at the corners when the mouse is over them).

The same problem has occurred on a completely new install of Ubuntu which I haven't altered anything.

Is there any way to stop this behaviour? After a few hundred times it gets pretty annoying.

---

### Post by gettinoriginal on 2009-05-16
By "full size", are you referring to full screen so that you are missing the title bar ??  First, check under view to make sure the full screen is not checked. Next, F11 twice, manually minimize window to preferred size, then close window.  Reopen window and maximize with max button.  This should fix the problem.  If you are just wanting windows to open to a specified size, manually choose size and then close window, after that, they should open in that size.  :p

---

### Post by Bark on 2009-05-16
> **gettinoriginal said:**
> By "full size", are you referring to full screen so that you are missing the title bar ??  First, check under view to make sure the full screen is not checked. Next, F11 twice, manually minimize window to preferred size, then close window.  Reopen window and maximize with max button.  This should fix the problem.  If you are just wanting windows to open to a specified size, manually choose size and then close window, after that, they should open in that size.  :p

Thanks for your reply. I've rewritten the question to clarify what I mean.

---

### Post by michy99 on 2009-05-16
It works like it is supposed to for me on 8.04. You must have a setting changed somewhere.

---

### Post by Bark on 2009-05-17
> **michy99 said:**
> It works like it is supposed to for me on 8.04. You must have a setting changed somewhere.
This happens on three different versions of Ubuntu on three different computers. The one I'm typing on now has exactly the same problem and was installed from scratch from a disk yesterday. I haven't changed anything.

---

### Post by gettinoriginal on 2009-05-17
Click the middle button (maximize/restore)so that it has one box, not 2 overlapping ones, and even though it stays full size, use the corner arrows by left clicking and dragging the window to the minimized size you want it set at.  (You can also move your cursor to the sides, top, or bottom and get the same arrows).  Once you have the size you want, close the window.  The next time you use the maximize/restore button, you should get the desired behavior.

---

### Post by Bark on 2009-05-17
> **gettinoriginal said:**
> Click the middle button (maximize/restore)so that it has one box, not 2 overlapping ones, and even though it stays full size, use the corner arrows by left clicking and dragging the window to the minimized size you want it set at.  (You can also move your cursor to the sides, top, or bottom and get the same arrows).  Once you have the size you want, close the window.  The next time you use the maximize/restore button, you should get the desired behavior.

Thanks, but I realized that my question was badly stated again. I've rewritten it slightly. The problem is that when I close the application at maximum size it doesn't remember its previous size when I open it again.

---

### Post by michy99 on 2009-05-17
Okay, here is how it works for me in 8.04. I have a window open which is less than maximum size. Let's say it is about a third of the screen. I click the middle button in the top corner and it maximizes the window. I close the window. I open it up and it is maximized. I click the middle button and it returns to the size it was before I maximized it the last time it was open.

This is how it works for me, and if I understand you, the way you want it to work for you. I have know idea why it doesn't, but I wanted to make sure that I understand what you are saying and to say that it works fine for me.

---

### Post by pastalavista on 2009-05-17
I've noticed this problem too and it is, as you say, annoying. I think the error is in the window managers and/or gnome. I don't maximize windows any more except fullscreen (F11). It ususally returns to the small window if I don't use the maximize button. Sometimes F11 doesn't even work but the selection "Fullscreen" in the 'view' menu does. Buggy bugs for programmers. They do a bang-up job for free.

---

