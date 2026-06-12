---
title: "Weird animation on login"
date: 2006-06-16
forum: Desktop Environments
---

### Post by jejones3141 on 2006-06-16
This morning marks the second time I've seen a weird animation when I try to log in.

There were many GNOME-related upgrades this morning (and kernel, too, for that matter). I upgraded, made a point of grabbing the new linux-restricted-modules-k7 (why that doesn't get done automatically is a question for another thread...), and restarted.

The nvidia proprietary driver started up fine, and I logged in.

Then the screen went white, and a little animation appeared in the center of it: it showed a mouse (rat?) running in a little cage made up of the Ubuntu logo.

After that ran for a while, it went away, and I got a complaint about a button being unconfigured, and then a panel that only covered the top left-hand corner of the screen, with the unconfigured button on it.

It must be something that new GNOME doesn't like about my configuration, because failsafe GNOME behaves pretty well normally. Is there a log file I can look at to see what is failing to work? In the short term, I suppose I can just

for i in .gnome*
do
    mv $i $i.barf
done

start fresh, and then put things back the way I want, but I'd like very much not to have to do that. Any suggestions would be appreciated.

---

### Post by pyromithrandir on 2006-06-16
The animation you're describing sounds like the XFCE login... are you sure you're logging in to gnome?

---

### Post by jejones3141 on 2006-06-16
[QUOTE=pyromithrandir]The animation you're describing sounds like the XFCE login... are you sure you're logging in to gnome?[/QUOTE]

Hmmm.... I didn't *think* I'd changed my default session... but I explicitly chose just plain GNOME, and it worked. (Scratches head...) Thanks!

---

### Post by Indifferent on 2006-06-16
Yes, that is the screen I get while booting into Xfce.

---

