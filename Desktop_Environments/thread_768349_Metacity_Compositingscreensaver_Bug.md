---
title: "Metacity Compositing/screensaver Bug"
date: 2008-04-26
forum: Desktop Environments
---

### Post by schtufbox on 2008-04-26
Hi, I'm using Ubuntu 8.04
I disabled compiz, sure it looks nice, but to me it's overkill, and also unless I disable it before running a 3d game it costs me in FPS.
Anyway, I enabled compositing for metacity (via gconf-editor) and I get some effects without the nasty fps cost of compiz. Shadows, proper transparent console etc.
There is a slight bug however. If you lock the PC, or the screensaver comes on..when you unlock and go back to desktop, sometimes it's darker than it should be, faded check this screenshot: [http://img115.imageshack.us/my.php?image=allgonedarkxg0.png](http://img115.imageshack.us/my.php?image=allgonedarkxg0.png)
See what I mean? The problem also stacks, I let the screensaver come on a good few times in that pic, so normally it's not THAT dark. This doesn't ALWAYS happen, only if the screensaver has been on for a while. 
Logging out then back in fixes it, but no need for that as I can do:
```
pkill metacity && metacity --replace 
``` to fix the darkness.
Just wondering if anyone else has this issue, and figured out how to prevent it from happening at all.
If it is relevant I have a gefore 7300GT video card, running at 1440x900 resolution, using the latest drivers as installed by EnvyNG, I have no other problems with Hardy whatsoever :)

---

