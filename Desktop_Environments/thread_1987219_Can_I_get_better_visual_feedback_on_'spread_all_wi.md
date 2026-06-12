---
title: "Can I get better visual feedback on 'spread all windows' view"
date: 2012-05-26
forum: Desktop Environments
---

### Post by pedrotuga on 2012-05-26
I'm rather picky when it comes to desktop environments. A good launcher and a good task switcher is all I ask, but it turns out that that's not that easy to get.

The deskbar applet, my all time favorite launcher has been discontinued. After trying out pretty much every alternative out there, my preference is on ubuntu's dash.

I'm not a big fan of the whole fancy desktop trend (unity, gnome shell, cinamon, etc.) however, I must say that I'm rather impressed with unity, and I think I'll stick with it on my personal computer.

What I'm missing the most is more window switching power. I like unity's alt+tab implementation, but when working many windows, sequential access to other windows becomes ineffective. I would use Super+W in that case. The problem is that it's very difficult to see which window has focus in the 'spread all windows' view.
Is there any configuration that I could change to improve this?
A move vivid border around the active window or stronger shade on the inactive ones would be very helpfull.

---

### Post by zombifier25 on 2012-05-26
When you say "active windows", you meant the windows being selected or the last windows you are on before spread? If former, then go to ccsm > Scale > Opacity then set to the value you want. The nonselected windows will be transparent. If that still doesn't do you good, enable "Scale Addons", go to Appearance tab and enable highlighting.

If the latter, well I don't know. But after activating Scale, the Opacity trick like above works if you haven't moved you cursor a single pixel. Then again, you can simply press Super + W again to exit Scale.

---

### Post by pedrotuga on 2012-05-26
Yes, I mean the window being selected.

But what' is the 'ccsm'?

---

### Post by zombifier25 on 2012-05-26
It's the CompizConfig Settings Manager. Install it first:
```
sudo apt-get compizconfig-settings-manager
```

---

### Post by pedrotuga on 2012-05-26
scale > opacity did the trick.
Thank you. I was in need of this quite badly.

---

