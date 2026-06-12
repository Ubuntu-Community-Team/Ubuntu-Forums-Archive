---
title: "Dual Monitors on Gutsy"
date: 2007-10-17
forum: Desktop Effects &amp; Customization
---

### Post by shanlot751 on 2007-10-17
Hey, my pc isn't fantastic but it gets me by. I'm trying to set up dual monitors on gusty RC1 and it's not working out too well for me. I'l enabled both monitors and told it to "extend" the desktop to the second. Through the new control panel entry. I've tried both proprietary and open source nvidia drivers. I am running compiz though even when it's off I don't have much luck (I have'nt tried turning it off then logging in and out yet though) I have an nvidia geforce mx 5400 agp and a geforce 5600 pci to 2 crts. Anyone care to explain what I'm doing wrong?

---

### Post by _simon_ on 2007-10-17
I used nvidia-settings to set up dual screen on my 7900GS and I've seen other people post saying this was how they got theirs working.

You will need to back up your xorg.conf first and then run sudo nvidia-settings otherwise the changes won't be saved.

---

