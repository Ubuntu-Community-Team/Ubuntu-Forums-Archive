---
title: "Can't get compiz to work"
date: 2009-01-29
forum: General Help
---

### Post by billy61 on 2009-01-29
hey guys, i am having some problems getting compiz to work.
when i go to 
System->Preferences->Appearance->Visual Effects
and try to select anything other than "None" i get an error saying
"The Composite extension is not available"

Im running 8.10 and dual nvidia 8800 gts's (non-sli) with the 177 version nvidia drivers.

compiz-check doesn't support multiple video cards so that wont run to check whats wrong.

any suggestions?

---

### Post by johnjohn2 on 2009-01-31
Remove one of the cards and try compiz, it that works then you have found the answer.

---

### Post by billy61 on 2009-02-02
Its solved... kinda. Or at least the source of the problem is known:
You cannot use Xinerama with Compiz.
This lead me to a few options for my two monitors and tv:
1) run three seperate x screens.
2) use xinerama and link all three together, but dont use compiz
3) link two together through nvidia dualview, and then run a seperate x screen for the other one.

I chose #3 in the end, and have both of my monitors on one card and one X screen, and then i have my tv on a seperate card and x screen.

I don't know why xinerama and compiz cant be used together, but if they ever can, i'll be the first to use it.

---

