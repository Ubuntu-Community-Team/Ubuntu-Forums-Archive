---
title: "Having trouble with emerald"
date: 2008-03-25
forum: Desktop Effects &amp; Customization
---

### Post by kittiphanh on 2008-03-25
Ok, so I have gotten Compiz and Emerald installed. Only problem is that when I type in compiz --replace all my title bars disappear and I have to type in xfwm4 --replace to get it all back. I also have emerald and emerald-themes installed but that doesn't seem to work either, I tried both emerald --replace (which does nothing) and CCSM > Window Decoration > Command and typing in emerald but it still does nothing for me.

I have Xubuntu 7.10 with an Intel card. I know Compiz works on my computer b/c I have used it for Ubuntu. I have been searching for a way to fix this problem but it feels no one talks about Compiz on Xubuntu w/ the same problem I do.

---

### Post by Therion on 2008-03-26
This will stop Emerald from loading up with Compiz everytime you boot up and should solve your problem:```
mkdir -p ~/.config/compiz/ && echo USE_EMERALD="no" >> ~/.config/compiz/compiz-manager
```
Now, you **don't** want to use this if you want to use Emerald to decorate your windows.  If you're okay with using Metacity, then go for it.

---

