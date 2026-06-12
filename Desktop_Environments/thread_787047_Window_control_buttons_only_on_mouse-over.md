---
title: "Window control buttons only on mouse-over"
date: 2008-05-08
forum: Desktop Environments
---

### Post by Canterwood on 2008-05-08
Good day Ubuntu users/supporters!

I'm relatively new to Linux, I've been using OpenSUSE 10.3 in the past six months, but after a LAN-party for which I installed Windows, I decided to give Ubuntu a try. It works fine, drivers and proprietary software like codecs were all installed in a jiff, and even ndiswrapper practically configured itself (Big wow, it was a bitch in SUSE.). I've installed Compiz (At least that's what I call it, Ubuntu calls it advanced desktop effect settings), and Emerald to boot. Work great! I found a nice theme and it's doing fine.

However, I'd like to have the window control buttons to show up only on mouse-over, on this particular theme. How do I accomplish this? Any how-to's or someone who could point me to the correct configuration for this effect/setting?

Thanks a bunch in advance!

Canterwood.

---

### Post by Achtung on 2008-05-08
Click System/preferences/emerald theme manager.
Click the "Edit Themes" tab, and select the "Titlebar" sub-tab. 
Drop the "Button fill" and "Button outline" opacity setting to zero for active and/or inactive windows, depending on how you want it set up. 
Save your modified theme and restart X (ctrl+alt+backspace).

---

### Post by Canterwood on 2008-05-08
Dear Achtung,

This setting is a good idea, and it's actually already implemented in this theme. What I'd like to do is make the titlebar for the active window empty, until I hover my mouse over it (or over the control buttons).

Thank you for your input!

---

### Post by Achtung on 2008-05-09
I don't think you can get the titlebar text to appear when hovering over it with the mouse, like you can for the buttons. I've settled with a modified "Buttonless" theme with the title displaying only on the current active window (other windows display no title or buttons, but the buttons appear when I hover over them). 

If someone knows how to implement such a dynamic title bar, post here.

---

