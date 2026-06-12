---
title: "how do i stop compiz or emerald decorating my panel?"
date: 2009-05-30
forum: General Help
---

### Post by joesnose on 2009-05-30
Does anyone know a way to stop compiz, although i think it is actually emerald, decorating the top panel? It has a shadow, but i don't want it.

Thanks.


solved: post #4 has the perfect answer.

---

### Post by lovinglinux on 2009-05-30
You can edit the emerald theme to remove the shadow.

Applications >> Preferences >> Emerald Theme Manager

But the post #4 has a better solution

---

### Post by ZachS on 2009-05-30
f

---

### Post by ACMiller on 2009-05-30
The easiest way would be to exclude the panel from being shadowed in compizconfig settings manager. In the settings manager go to window decorations and attach the following to the end of the section on Shadow windows.

> | !(class=Gnome-panel)

Just so you know, I think compiz, emerald and metacity can all do window shadows (hence lovinglinux's solution) but compiz is the only one which shadows the panel. I've found it to also be the least buggy out of the three for shadowing.

Hope that helps
Cheers

---

### Post by WatchingThePain on 2009-05-30
In the settings for compiz there's an option to turn off shadows.
I can't remember where exactly.
You type in a little command in the box.
It's on Google and I only did it for Conky to look better but it turns off all shadows.

Compizconfig settings manager window decoration shadows, I put something like (any) & !(class=Conky) & !(class=Gnome-panel)

---

### Post by joesnose on 2009-05-31
thanks all for your suggeestions. 

This one works perfectly

> **ACMiller said:**
> The easiest way would be to exclude the panel from being shadowed in compizconfig settings manager. In the settings manager go to window decorations and attach the following to the end of the section on Shadow windows.

Quote:
| !(class=Gnome-panel) 




Cheers


cheers.

---

