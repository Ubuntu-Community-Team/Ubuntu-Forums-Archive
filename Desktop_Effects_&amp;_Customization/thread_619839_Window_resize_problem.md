---
title: "Window resize problem"
date: 2007-11-21
forum: Desktop Effects &amp; Customization
---

### Post by Monstroxus on 2007-11-21
My windows seem to forget their positons and size. I.E. When I load up Firefox or any other program its 99% of the time maximised (or full screen), even when I click un-maximise it remains full screen until I manually resize it. (when running Compiz Fusion + Emerald)

Is there something im missing in a configuration file that will make all my windows remember their position? Any setting in the compiz setting manager that I overlooked?

---

### Post by MrFuji on 2007-11-23
I'm having a similar problem.
My windows also forget their unmaximized state, but only if I close a window while it is maximized (not always though, I think it depends on when it was last "unmaximized"). I'm having this problem since... yeah, since the whole 3D desktop thing started (thus, with Compiz, Beryl and now compiz-fusion) and never found a solution, nor any topic where someone had the same problem... till now, obviously.

At the moment I'm fixing this partly with the help of some window rules in compiz, but it's not that elegant...

Oh, and of course, this does not happen with metacity...

Are there more out there with this problem? Try it out, open and close your firefox window a few times in its maximized state... If so, then I would say that this is a compiz bug...

---

### Post by elusivespoon on 2008-04-03
I'm also having a problem where windows don't remember their size after being closed, that started with Compiz. All windows open maximized, regardless of prior size. I've been digging for solutions for a while, but found none. Any ideas?

---

### Post by Monstroxus on 2008-04-07
Anyone?

---

### Post by chewearn on 2008-04-07
Ok, check this setting:
CCSM > Place Windows > Placement Mode

Is it "Maximize"?  Change to "Smart".

---

### Post by elusivespoon on 2008-04-23
AstalaVista, that was the problem. Though I'm not sure how the placement mode got switched to Maximize since I've never even bothered with that setting before . . . weird. Thanks.

---

