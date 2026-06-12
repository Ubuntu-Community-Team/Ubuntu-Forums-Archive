---
title: "Mirror two of three monitors? Or co-locate two?"
date: 2015-12-27
forum: Desktop Environments
---

### Post by SimonHGR on 2015-12-27
Hi all,

I have a laptop, I add an external (HDMI) display, with the same resolution as the internal display. Then I add a second external (VGA) display. Using the display config, I can easily have all three mirrored, or I have all three independent. However, I need the two HD displays (one being the internal one) to be mirrored, while the external VGA provides extra workspace.

I'm pretty sure I can't do this from the GUI, but I'm also fairly sure it should be possible to do it somehow (I once had a temporary weirdness that caused two of the three to be partially overlapping, but the GUI energetically rejects an attempt to do this deliberately.)

Any suggestions? What config files affect this? Can one disable the GUI based behavior if trying to take over manually? This is quite an important feature for presenters who want to drive an external projector, know what's on that projector while facing the audience, and simultaneously have some "private" workspace for preparation, notes, etc.

Thanks!
Simon

---

### Post by SimonHGR on 2015-12-28
I seem to have fixed this. I don't know if this is the "right" way, but I managed it using xrandr.

My three monitors are the internal, called eDP1, then HDMI1 which is the one I want to mirror, and VGA1 which is the one I want for "private workspace. I issue:

[FONT=Courier New]xrandr --output HDMI1 --same-as "eDP1"
xrandr --output VGA1 --right-of "eDP1"[/FONT]

and the result is mirroring between the HDMI display and the internal, and the auxiliary is off to the right, just as desired :D

---

