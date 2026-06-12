---
title: "Subpixel smoothing does not work for most non-default fonts"
date: 2010-10-25
forum: Desktop Environments
---

### Post by kimhyunkang on 2010-10-25
After I installed maverick meerkat on my laptop yesterday, I found out that subpixel smoothing only works for specific fonts.
Subpixel smoothing works great with Ubuntu, Sans, Serif and Monospace (which is really bad for a coding font) fonts but does not work with any other fonts installed with the distro.
I tested with a few other fonts from apt-get like ttf-bitstream-vera or ttf-droid but they all had the same problem.
Does anybody know how to fix this? Or I have to go back to my old lucid lynx. (which worked great on this machine)

If this helps, my laptop has a 32-bit intel Core2Duo CPU and an nvidia video card.

Solved: This was a Korean-locale specific problem. If you have a same problem, in system language preferences panel, move &#54620;&#44397;&#50612;(&#45824;&#54620;&#48124;&#44397;) to second place (under &#54620;&#44397;&#50612;) then problem is solved after next login.

---

