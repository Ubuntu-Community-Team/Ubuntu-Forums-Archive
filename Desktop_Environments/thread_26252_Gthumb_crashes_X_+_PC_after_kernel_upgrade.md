---
title: "Gthumb crashes X + PC after kernel upgrade"
date: 2005-04-12
forum: Desktop Environments
---

### Post by remmelt on 2005-04-12
Hello!

I have recently upgraded my kernel from 2.6.10-5-k7 to 2.6.11-1-k7. Since that upgrade, whenever I open gthumb and click on anything, X freezes. I can't quit it by ctrl-alt-backspace, I can't switch to a terminal or anything. The only thing that works is alt-sysrq-b for immediate reboot.
No such problem with the old kernel though, I still have it installed and when I boot that one, everything's a go.

Any idea what this can be?

I compiled a driver for my webcam with the new kernel's sources, and modprobed it in, could it be that that's bothering me?

---

### Post by remmelt on 2005-04-12
hmm. I've rmmoded the videodev and spca5xx modules that comprise the webcam driver and it still hangs.
It also hangs sometimes when I'm not doing anything specific, typing in Eterm or sth... Very weird.

For the time being, I'm back on the older kernel.

I'm running the ATi fglrx driver as found in the Hoary howto, ATi v0.2 post. Any other information I can post that could be helpful?

---

### Post by remmelt on 2005-04-13
anyone?

---

