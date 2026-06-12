---
title: "[SOLVED] Not all clicks &amp;quot;register&amp;quot; when rapidly clicking"
date: 2007-08-13
forum: Gaming &amp; Leisure
---

### Post by noerrorsfound on 2007-08-13
When playing AssaultCube, rapidly clicking with the pistol in an attempt to fire as fast as possible results in slow firing. I guess when I click a lot, some clicks are lost and don't "register" with the game or whatever handles input.

I didn't have this problem playing the game in Gentoo, and I could fire the pistol in rapid succession.

**Solution:** Edit /etc/X11/xorg.conf and change "Emulate3Buttons" to *false*.

---

