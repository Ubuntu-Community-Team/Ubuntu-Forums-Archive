---
title: "Firefox windows open with top windows border off screen"
date: 2009-04-27
forum: General Help
---

### Post by mister harbies on 2009-04-27
Hi fellow Ubuntians,

Since upgrading my ASUS from 8.10 to 9.04 I have had all my firefox 3.0.9 windows opening with the top of the firefox window showing off the screen at the top. This means if I want to access my menu bars, I must use alt+mouse to drag a window down (like I now do with all windows). I do not see the top of the window including the close/minimise/maximise buttons, and the menu bars.

Before the upgrade to 9.04, Firefox was always opening windows to align with my top gnome panel... seamless :) ... but no so now :(

Im also running compiz if this helps

---

### Post by slibuntu on 2009-04-27
Maybe delete your top panel and re make it? Might make firefox realise it is there and not appear under it.

---

### Post by mister harbies on 2009-04-27
Moving the panel to the right, and opening firefox, only the top of the window appears off screen. Seems that the gnome panel is not to blame. I do not see my window borders, but I do see the firefox menu bar (since the panel was moved).

---

### Post by kerry_s on 2009-04-27
have you tried making it smaller(right-click taskbar>resize), then closing it, then opening and maximizing?

---

### Post by mister harbies on 2009-04-27
Maximised firefox windows are fine, but I don't like to browse with a maximised window. The problem also happens with dialog boxes, new windows, the add-ons, downloads and preferences windows.

I have tried maximising, changing the size of the window

---

### Post by mister harbies on 2009-04-27
Ahhh! I solved it. A setting in Compiz Manager. Placed Windows had a rule for firefox to open windows 0 pixels x 0 pixels away from the top left corner, but somehow the compiz thinks the top of the window is a few more pixels higher than it should be.

---

