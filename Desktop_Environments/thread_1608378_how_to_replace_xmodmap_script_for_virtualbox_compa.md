---
title: "how to replace xmodmap script for virtualbox compatibility?"
date: 2010-10-29
forum: Desktop Environments
---

### Post by dewdrop_world on 2010-10-29
I'm looking for someone with X11 keyboard-mapping savvy to advise how to handle a couple of requirements.

1. Currently I'm using xmodmap to switch the modifiers so that alt is ctrl, super is alt, and ctrl is super -- moving ctrl next to the space bar so it's less effort to reach (and is a lot friendlier for Emacs). This has been fine except for...

2. I got fed up with NaturallySpeaking under wine, so I installed it under virtual box. That's working beautifully -- I'm *delighted* with the performance compared to the crashiness with wine -- BUT... my xmodmap script causes virtual box to fail to identify the active keyboard layout, and it substitutes some random weirdo layout I never saw before. The workaround is to unplug the keyboard and plug it back in, and boot up the virtual machine. Then I can redo xmodmap and the virtual machine continues to run with the right layout.

That won't work for me all the time because it's a laptop and I don't always use it with an external keyboard. If I don't have one around, I'll have to log out and log back in at least, or maybe even reboot, to clear the modifier mappings. That's a disruption in workflow I wouldn't be quite happy with.

I've seen some threads on the virtual box forms indicating that Oracle have no interest in supporting modifier remapping, so the question is -- is there a way to incorporate the new modifiers into the xkbmap itself?

Thanks --
James

---

