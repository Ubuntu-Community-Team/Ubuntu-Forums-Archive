---
title: "dual monitor gameing issue"
date: 2008-04-03
forum: Gaming &amp; Leisure
---

### Post by c0d4041292 on 2008-04-03
hi, i just setup a 2nd monitor on my comp and when i try to play games it streches it across both screen, ive read a couple other post but they are telling of ways to make it appear on only one monitor manually....i was wondering if there was an automated way of doing this

---

### Post by Hobo Joe on 2008-04-03
Set the game to the resolution you like, and set it to windowed mode. Then, set a hotkey for 'set fullscreen', with your window manager(Located under System > Preferences > Keyboard Shortcuts).

Then, launch the game, and once it's loaded, just press the hotkey and you're set!

---

### Post by supertux on 2008-04-04
Or, with a nvidia graphics card  you can specify metamodes in xorg.conf:

    Option         "metamodes" "DFP-0: nvidia-auto-select +1680+0, DFP-1: nvidia-auto-select +0+0; DFP-0: null, DFP-1: nvidia-auto-select +0+0"

---

