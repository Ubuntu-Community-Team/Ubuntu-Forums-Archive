---
title: "Expo in Unity/Compiz"
date: 2011-04-09
forum: Desktop Environments
---

### Post by Little Bones on 2011-04-09
Howdy,

In 10.10, when you would use the expo from the unity launcher, it would separate all of the windows in every view for easy movement, however by default in 11.04 they're all stacked on one another. Is there any way to change this at this time?

Thanks,

LB

---

### Post by Copper Bezel on 2011-04-09
Unity 10.10 did that? Wow, that's kind of cool. It's like Scale and Expo at the same time.

The backend for Unity in 11.04 is completely different from that in 10.10, now based on Compiz, a much more complete compositor and workflow system than the newer Mutter used in 10.10. If you install Compiz Config Settings Manager

```
sudo apt-get install ccsm
```

you can run the command ccsm to configure some of the settings, but Expo doesn't have that option at present. You might consider playing with the Scale plugin, though, which you can configure from the same package and which can be set to show all windows from all workspaces (but laid out in sequence on the present workspace.)

Edit: Interestingly, KDE's KWin also lays out the windows Scale-style in each workspace of the Desktop Grid plugin (the equivalent of Compiz's Expo.) The perk of Compiz's method, I guess, is that windows can be positioned on each workspace, rather than just being moved between them, from the Expo view, but I think I like this other behavior more.)

---

