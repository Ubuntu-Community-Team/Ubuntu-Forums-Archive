---
title: "Quake 4 switches to windowed mode and Ubuntu hanges"
date: 2010-03-18
forum: Gaming &amp; Leisure
---

### Post by 61e@4 on 2010-03-18
Sorry, English is not my native language, by i'll try to explain myself as clear as possible.

I use Ubuntu 9.04 and just have installed Quake 4. Everything works fine but one annoying thing. When i try enter restricted areas the game switches to window and then i can't use nor my keyboard, nor mouse at all, while the game is still working.

Example: there is an episode when a large ship is landing. While it is landing it is not possible to enter the area under the ship, but after it had landed you have to go under it. So if i try to enter the area under the ship while it is landing tha game switches to windowed mode and then i can watch the process of ship's landing but can't do anything. For that reason i have to reset my computer.

Another example: in earlier episode i have to use a cannon to blow up the gate. If i click to enter the cannon before it is actually possible - the same thing happens and i have to hard reboot my computer.

And this happens for every temporary restricted area in the game.

Does anybody know what it is about and how to fix this behavior?

At least, maybe i just don't know an appropriate key combination to switch out from the game or close it or do something else that'll help not to reboot a computer with a reset button...

Thanks for any help!

---

### Post by Brebs on 2010-03-20
> **61e@4 said:**
> switches to window
Try pressing Alt+Enter - that's the usual key combination to toggle windowed mode.

Show the resolutions supported, by running:

xrandr

---

### Post by 61e@4 on 2010-03-22
> **Brebs said:**
> Try pressing Alt+Enter - that's the usual key combination to toggle windowed mode.

Show the resolutions supported, by running:

xrandr

Thank you for advice!

I attached to this post a text file with output from xrandr.

Alt+Enter didn't work for me. But now i already don't have to reset my computer. :)

Well, the last time when quake4 switched to windowed mode and frozen my desktop, it was in the middle of a battle (and i became a static target for attackers) , so it happens not only when trying to enter temporarily restricted areas. Or it just seems like that... 
So i pressed Ctrl+Alt+F1 and logged into command prompt. I ran 'top' and killed process quake4. After that i switched to GUI with Ctrl+Alt+F7. So a don't really have to reset my computer. Well, i am noob in Linux so it makes me happy that i learned something new about it.
For now what i would want to know is why smoothly running game behaves so strange. Is there any reasonable method that i could use to reveal the mystery?

By the way when i entered GUI desktop after killing the game's process, i found that the game left an output in terminal window from which i ran the game. It is attached too. The question is: how is possible to capture all output that comes from the start  of the game to a text file while restricting a text file size to a reasonable value? I understand that it may be not possible to really capture all output with a size restrictions applied, but it acceptable if it is configurable.

---

### Post by juancarlospaco on 2010-03-23
**killall gnome-screensaver**

---

### Post by Brebs on 2010-03-23
I assume you're using an nvidia card. I don't recall seeing this issue reported before, but there are some things that spring to mind:

1. Turn [DynamicTwinView off](http://forums.gentoo.org/viewtopic-t-528285.html), so xrandr reports the correct 60 instead of wrong 50 (quake4 runs at 60fps, or 30fps if slowed down).

2. Enable [NoFlip](http://forums.gentoo.org/viewtopic-t-535450.html), because flipping isn't stable, and made quake4 occasionally hang for me.

3: And the other things I mention in the NoFlip thread:
export __GL_YIELD="NOTHING"
export __GL_DOOM3=1
export SDL_VIDEO_X11_DGAMOUSE=0

And try these 2 also:
set com_fixedtic 1
set com_syncgameframe 1

Also try upgrading your [nvidia driver](http://www.nvnews.net/vbulletin/showthread.php?t=122606).

---

