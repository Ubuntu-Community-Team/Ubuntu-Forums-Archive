---
title: "Feisty Screensaver - Dark Screen Upon Return"
date: 2007-04-25
forum: Desktop Environments
---

### Post by muecker on 2007-04-25
I just installed a new ATI X1550 card on my home machine under Feisty.  I'm using the fglrx drivers from the repository.  The video looks real good until it returns from the screensaver, after which the screen is dark.  Not black, but dark enough to be difficult to see.  It seems to do this every time it returns from the screensaver.  Any idea why it does this and what I need to fix?  Thank you.

---

### Post by reignbow on 2007-04-26
I have the exact same problem, both with the screensaver and with the lock screen function. I have excluded DPMS as the source of the problem. A full restart of gdm is needed to get the screen back to normal. The colors change hue as well, which seems very odd to me.

---

### Post by muecker on 2007-04-26
I'm not sure if this bug is related or not.  I hope to try the ATI Control Panel at home tonight to see if that will get the screen back.

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/94019](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/94019)

Update: I just tested it and resetting the Gamma control using the ATI Control Panel is enough to restore the screen.

---

