---
title: "[LXDE] Taskbar height not expanding"
date: 2012-10-03
forum: Desktop Environments
---

### Post by gsrgsrgsdg on 2012-10-03
Hello,

I have a problem with the taskbar (window list) in LXDE (latest Lubuntu release).

The window list doesn't expand to the full height of the taskbar, meaning that when my mouse cursor is at the very bottom of the screen i can't switch windows.

Here are 2 screenshots to illustrate the problem:

[IMG]http://i.imgur.com/b4TGH.png?1[/IMG]

The cursor is at the very bottom of the screen, note how the panel is not active

[IMG]http://i.imgur.com/asrcy.png?1[/IMG]

The cursor is slightly higher, now the panel has become active.

How can i fix this?

---

### Post by ankspo71 on 2012-10-03
Hi, 
By default the panel height is 26 pixels high, but the icons on the panel are 24 pixels high. If you decrease the size of the panel by 2 pixels, or increase the size of the icons by 2 pixels, the problem should disappear. The icon height is also the panel applet height.

Right click on the panel and choose Panel Settings. Then when the Panel Preferences window appears, look in the geometry tab for "Height" and "Icon" and give them identical values.

---

### Post by gsrgsrgsdg on 2012-10-03
Thanks, I've decreased the panel size to 22px (to match the 22px icon size), works like a charm :)

---

### Post by vasa1 on 2012-10-03
Nice QnA. It took me some time to understand what OP wanted but I finally got it. I'm going to try this trick with a vertical panel.

OP, if you do look at this thread again, please mark it [SOLVED] by clicking on Thread Tools near the top right of this page and choosing the appropriate option from the dropdown.

---

