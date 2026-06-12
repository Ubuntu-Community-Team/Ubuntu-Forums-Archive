---
title: "compiz running but no Windows manager?"
date: 2008-12-20
forum: General Help
---

### Post by ashkev on 2008-12-20
I have moved to kubuntu and have compiz running, but all of my windows are missing the windows controls (the part with minimize, maximize, close)  In gnome, I know that this was controlled by the emerald themes, but I am not sure what I need to do in KDE to fix this.

Thanks

---

### Post by snova on 2008-12-20
I don't know how well Compiz interacts with KDE. At any rate, a lot of the things Compiz does are built in to Kwin- and more is to come with KDE 4.2.

But, try this. Press Alt-F2 (or whatever the key combination is to Run Program, I changed it and don't remember the default) and type "compiz".

If it doesn't work for some reason, replace "compiz" with "kwin", the default window manager.

It's only a temporary solution...

---

### Post by Farmer of Bricks on 2008-12-22
> **snova said:**
>  Press Alt-F2 

Alt-F2 is reassigned by Conky to another function, so click on your Kmenu, Launcelor, or other menu variant, and open a console. 
type:
```
krunner
```
and hit return.
in that box that just popped up, type:
```
emerald --replace
```

Does this help?

---

### Post by snova on 2008-12-22
> **Farmer of Bricks said:**
> Alt-F2 is reassigned by Conky to another function, so click on your Kmenu, Launcelor, or other menu variant, and open a console. 
type:
```
krunner
```
and hit return.
in that box that just popped up, type:
```
emerald --replace
```

Does this help?

That seems like a pretty roundabout way to do it. Why not just run 'emerald --replace' in the terminal? :P

---

