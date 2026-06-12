---
title: "Desktop icons disappeared in gnome-tweak DE after update in 13.10"
date: 2014-04-23
forum: Desktop Environments
---

### Post by Luxx on 2014-04-23
A solved this and thought I would post it in case someone else had it happen to them.
The fact that I am using the gnome-tweak-tool with the classic gnome look is probably relevant. 
I've noticed I have a hard time finding fixes for things because my issues are weird because of the DE plugins.

I got the Software Updater message this morning telling me new updates were available and I allowed the update.
Suddenly my desktop icons were gone. The only way I could bring them back was to start nautilus in terminal, but it they would disappear again as soon as I closed the terminal. I thought it was a nautilus issue, however, it seems it was actually a compiz issue. I fixed it entering the following in the terminal:

```
dconf reset -f /org/compiz/
```

---

