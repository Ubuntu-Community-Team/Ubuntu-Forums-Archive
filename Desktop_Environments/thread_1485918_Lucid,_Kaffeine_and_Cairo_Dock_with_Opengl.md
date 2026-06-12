---
title: "Lucid, Kaffeine and Cairo Dock with Opengl"
date: 2010-05-17
forum: Desktop Environments
---

### Post by TheValk on 2010-05-17
I have a clean install of Ubuntu 10.04 with an Nvidia graphic card.  I like Kaffeine for its TV tuner capabilities so I have installed it from the repos.
I also have Cairo Dock installed.
If I start the computer with Cairo Dock no opengl everything is fine but if I start it with Cairo Dock opengl option then Kaffeine runs with a transparent window rather than showing the picture although sound is fine.

Is this a known bug?

---

### Post by fabounet on 2010-05-17
yes it's a known bug inside **Qt**
the devs don't care about it, but there is a workaround :
start your program with 
```
export XLIB_SKIP_ARGB_VISUALS=1 && Kaffeine
```

Same for Skype and any program using Qt.

---

### Post by TheValk on 2010-05-18
> **fabounet said:**
> yes it's a known bug inside **Qt**
the devs don't care about it, but there is a workaround :
start your program with 
```
export XLIB_SKIP_ARGB_VISUALS=1 && Kaffeine
```

Same for Skype and any program using Qt.

Many thanks.
This fixed the problem and now I can have all the Cairo-Dock goodness as well as my TV shows.

---

