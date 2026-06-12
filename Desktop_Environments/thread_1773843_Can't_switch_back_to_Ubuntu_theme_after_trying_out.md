---
title: "Can't switch back to Ubuntu theme after trying out Kubuntu"
date: 2011-06-02
forum: Desktop Environments
---

### Post by DiceRules on 2011-06-02
Hi, all.

To the best of my recollection, here's what happened.

I installed Ubuntu 10, all default options.  No custom themes.  Using Gnome.

I installed Kubuntu.  Again, all default options.  Still using Gnome, though.

I upgraded to 11.

Then, when I try to switch back to Ubuntu, I can't get the default Ubuntu theme to stick.  When I log in, it looks correct for about twenty seconds, then everything switches to Ambiance or Plymouth or something else.

Basically, I'm trying to get the brown task bar back and I can't.  It's all light-colored.

Any ideas?

---

### Post by Copper Bezel on 2011-06-02
It may be related to a previous problem with Gnome Settings Daemon, although this doesn't seem to be a problem with 11.04 in the way it was with 10.10, making this a little unusual. What happens if, after the theming crashes, you run 

```
killall gnome-settings-daemon
gnome-settings-daemon
```

Just so you know, the default theme *is* Ambience, and what you're seeing is probably GTK+ without theming applied.

---

### Post by DiceRules on 2011-06-02
My new best friend is Copper Bezel.  Thank you!  :-)

I did this but didn't find anything meaningful (to me) in the logs:

```
sudo grep -R gnome-settings-daemon ./*
```

Do you think this is the same bug you mentioned?  Is it worth my reporting it?  Anything I can do to prevent it?

---

### Post by Copper Bezel on 2011-06-04
It's a known issue, but one that the devs are having some trouble with, apparently. The fix I would have suggested would be to just put that pair of commands above in your Startup Applications after a delay, but you can try [this guide]("http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html") to fix the problem a little closer to the source.

---

