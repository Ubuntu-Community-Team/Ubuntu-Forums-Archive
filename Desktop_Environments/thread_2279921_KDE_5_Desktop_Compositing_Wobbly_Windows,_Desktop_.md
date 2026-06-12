---
title: "KDE 5 Desktop Compositing: Wobbly Windows, Desktop Cube and Magic Lamp not available"
date: 2015-05-26
forum: Desktop Environments
---

### Post by alikazmi-2040 on 2015-05-26
Hello,

With Kubuntu 15.04, KDE Plasm 5 has suddenly decided that certain desktop compositing effects are no longer available to me. I have hybrid nvidia GeForce GT 740M and intel 4600M GPUs on this laptop and while both are powerful enough to handle compositing, the effects are available with neither. I am using the proprietary nvidia 346.59 drivers.

The effects were available and working perfectly fine up till a couple hours ago. The only possible reason for them becoming unavailable that I can think of is using the nomodeset option in grub to debug hibernation issues (which resulted in secondary monitor getting completely ignored and some graphical glitches).

I would really appreciate if someone has a solution for me because I am not even sure how to go about debugging this problem. If nothing else, I'd really grateful if someone could point me in the right direction on how to debug this issue and hopefully resolve it.

Cheers

---

### Post by alikazmi-2040 on 2015-05-26
Since the entry for Desktop Effects doesn't have an Advanced tab anymore (at least on my system), I didn't realize that kwin backend had been switched to xrender. In case anyone else runs into this issue, go to /home/<username>/.config/ and open kwinrc in kate (or any other editor of choice), look for Backend=xRender and change it to Backend=openGL. Once you log back into KDE, you'll have all the effects available.

---

