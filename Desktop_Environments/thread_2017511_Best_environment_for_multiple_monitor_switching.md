---
title: "Best environment for multiple monitor switching"
date: 2012-07-05
forum: Desktop Environments
---

### Post by Only1KW on 2012-07-05
I have Ubuntu Oneiric installed on my laptop at work (I plan to move to Precise ASAP, but work applications don't support it yet and aren't scheduled to until September).  At work, I am constantly moving between my office, where I have an external LCD screen, and conference rooms, where I use the built-in display and sometimes also connect to a projector if I am presenting.  I have an Nvidia adapter and use the Nvidia-settings application to place the display in Twinview mode and switch between the different displays as needed.

I'm currently using KDE as that is my preferred environment, but KDE (and more specifically, Plasma-desktop) doesn't handle switching between displays very well.  When just switching between my external LCD screen and the built-in display, KDE seems to work well most of the time, though seemingly randomly every once in a while Plasma-desktop will crash or hang.  However, if I add a different display to the mix, Plasma-desktop is almost guaranteed to crash or hang.  The only way I've reliably recovered from this is to restart the kdm service (though occasionally even this doesn't work).  Just stopping and restarting Plasma-desktop does not help.   I've also encountered issues with Plasma-desktop crashing/hanging when attempting to move a panel around on the screen.

Can someone recommend a combination that has worked for them stability-wise on Ubuntu (not necessarily using KDE though)?  I'd prefer that all monitors in the configuration make up one contiguous display so that if I disconnect the external LCD monitor, I don't lose access to those applications on that monitor until I reconnect the monitor again.

---

### Post by 3Miro on 2012-07-05
I am switching monitors constantly, although I have Intel HD 3000. I am using Unity, but I would think plain Gnome 3 should work well enough. In my experience, XFCE and OpenBox are not as robust in changing monitors, but they may also work well for you.

---

### Post by Only1KW on 2012-07-05
What are you using to resize your desktop as needed for the different monitors?  Just xrandr?

---

### Post by 3Miro on 2012-07-05
Gnome 3 has a "display settings" tool which I think uses xrandr. But it is a nice graphical front-end, no need for CLI. XFCE has one too, although it is even more basic and I don't know if LXDE has one or not.

Nvidia-Settings is more sophisticated, but it requires Nvidia.

---

