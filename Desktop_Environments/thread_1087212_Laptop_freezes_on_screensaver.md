---
title: "Laptop freezes on screensaver"
date: 2009-03-04
forum: Desktop Environments
---

### Post by xtiano77 on 2009-03-04
I have an Intel Dual Core laptop running Ubuntu 8.10, 32 bit.  Today, actually a few minutes ago, I did an update and downloaded two patches.  After that I restarted the computer and browsed the internet for a few minutes.  I locked up the screen and walked away.  Now my wife is trying to get into the computer, but the screensaver froze up and the password prompt will not come up when I click or move the mouse, and or hit enter, space bar, or click on Control + ALT + F1.  Are there any other set of key that can be pressed in order to bring the system back?  I don't want to press the power button and force a shutdown because the last time I did that, it was right after the install and the OS woun't boot up after that.  As always your help is greatly appreciated.

I also tried some combination of keys begining with ALT+PRINTSCREE, but nothing took. Eventually I pressed the Control+Alt+Delete for a few seconds and the system shut off.  Now, in addition to the scenario above, had the system given me a message that something was wrong with the booting process, what would the steps be in order to fix whatever files might have been corrupted as a result from the hard boot so I don't have to do a fresh install?  Thanks in advance for your help.

Oh, one last thing, this seems to happen on my laptop only.  I haven't had the misfortune of having my desktop freeze on me, even when using the same screensaver. The desktop is running Ubuntu 8.10, 64 bit. Any clues as to why this happens on one machine and not on the other?

---

### Post by rozbarwinek on 2009-03-05
Have you installed drivers for graphic card?

---

### Post by darinmiller@cableone.net on 2009-03-06
Using 64b 8.10, my Dell 1530 laptop started "freezing up" in screen saver mode after batch of updates that came down with kernel sub-version 2.6.27-12.  To clarify, "freezing up" means: unresponsive to keyboard or mouse input, yet everything else is running fine. I was hoping the next kernel sub-version release would fix it, but sadly 2.6.27-13 still has the same problem.

I am running NVidia's 180.35 drivers on an Geforce 8600M GT card.  The "lockup" problem also occurs when awakening from sleep when the screen saver option is enabled.  Also, the screensaver preview app locks up previewing screen savers. The only escape is ctrl-alt-backspace or a system power down/restart.

Edit....

I reverted back to the NVidia 180.29 driver and the screen savers work just fine.

darin

---

