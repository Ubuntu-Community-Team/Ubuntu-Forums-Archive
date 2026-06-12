---
title: "xmame.SDL not seeing keystrokes over VNC"
date: 2010-07-05
forum: Gaming &amp; Leisure
---

### Post by lordbah on 2010-07-05
In the basement is an arcade cabinet with Ubuntu 8.10 and xmame.SDL 0.106. Upstairs is a desktop with Ubuntu 10.04. From the desktop I open Remote Desktop Viewer to the arcade machine, because I want to change some DIP switch settings in one of the games and the arcade machine doesn't have a keyboard. But it isn't seeing tab, esc, or in fact any key. I can open a terminal and keys work fine there, so it's not just a VNC issue.

-gi (grabinput) confines the cursor to the xmame window but doesn't make keystrokes work.

I believe this used to work ... but I wouldn't quite bet the house on it.

Yes, the software is old, but it has been working so there has never been any incentive to move to sdlmame or upgrade.

---

### Post by disturbedite on 2010-07-05
don't use xmame. its been dead for years. use sdlmame (its part of mainline mame now).

---

### Post by hikaricore on 2010-07-05
> **disturbedite said:**
> don't use xmame. its been dead for years. use sdlmame (its part of mainline mame now).

You didn't read the post did you?
The issue isn't with xmame, it's with the op trying to configure it via vnc...

Honestly just hook up a keyboard to your system for 5 minutes and make the changes you need, it will save your sanity.

---

