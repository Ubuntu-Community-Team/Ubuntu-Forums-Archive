---
title: "Revert to default panels in Xubuntu 11.10"
date: 2011-10-27
forum: Desktop Environments
---

### Post by kkjaergaard on 2011-10-27
How do I revert to default panels in Xubuntu 11.10? I tried [http://ubuntuforums.org/showthread.php?t=771660]("http://ubuntuforums.org/showpost.php?p=4820582&postcount=4") without any luck; when I start the panel again, it looks the same.

It seems that the panel read configs from somewhere else.

---

### Post by gsmanners on 2011-10-27
> **kkjaergaard said:**
> It seems that the panel read configs from somewhere else.

Are you sure you followed the right instructions?

> ```
rm -fr ~/.config/xfce4/panel
killall xfce4-panel
```

Alt+F2 -> xfce4-panel

Gettting the two mixed up would result in no change.

---

### Post by kkjaergaard on 2011-11-01
> **gsmanners said:**
> Are you sure you followed the right instructions?

I think I did, but I'm not sure anymore. When I followed the instructions, the panels didn't revert to default - however, when I started my computer a few days later, the panels were reverted.

My lesson: Count to ten before posting ... :oops:

---

### Post by afrilas on 2011-12-25
I've done that but it just made it worse..

Now this is how my desktop looks like what should i do?

---

### Post by Toz on 2011-12-25
Try this instead.

First close the panel program.
```
killall xfce4-panel
```

Second, remove the existing config files:
```
rm -r ~/.config/xfce4/panel
```

Then restart xfce4-panel by pressing Alt-F2 and
```
xfce4-panel
```

---

