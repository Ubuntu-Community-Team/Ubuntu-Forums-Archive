---
title: "What would it take to get fluxbox to have effects when workspaces change"
date: 2007-11-19
forum: Desktop Environments
---

### Post by PurposeOfReason on 2007-11-19
With fluxbox there is no way to use compiz fusion or beryl for obvious reasons. However, one of the features I find to be useful is the cube and desktop plane as it gives you a bit more sense as of where your windows are. Is there any possibly way to get the source code the compiz uses for this and make it work with xcompmgr? Yes, I realize it's a pretty silly thing to ask.

---

### Post by MNICY on 2007-11-20
could you not get the source code from the compiz website?
[http://compiz.org/](http://compiz.org/)

---

### Post by winter_mute on 2007-11-20
I think what would need to be done would to fork Fluxbox.  The issue is that you'd be adding to the Window Manager, which would weigh down Fluxbox.  Honestly, you'd need to do some heavy coding to get Compiz-style effects in Fluxbox.  I'm not sure exactly what's needed, just that you'd have your work set out for you.

---

### Post by jviscosi on 2007-11-20
According to Wikipedia, Compiz is written in C while Fluxbox is written in C++ ... If that's accurate, you would definitely have a project on your hands trying merge procedural and object-oriented code together.

3ddesktop gives you a spinning cube and various other visual switching effects, but the windows aren't live previews; it just takes a snapshot of your current workspace when you activate it (I have it programmed to various hotkeys).  This means that if you also do desktop switching without using 3ddesktop, the snapshots will get stale.  However, if you're scrupulous about always using it or you always have it "acquire" when you fire it, then it might do some of what you're looking for without having to use compiz code.

---

