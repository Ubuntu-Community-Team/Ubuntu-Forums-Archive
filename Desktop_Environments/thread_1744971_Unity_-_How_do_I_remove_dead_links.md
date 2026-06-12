---
title: "Unity - How do I remove dead links?"
date: 2011-04-30
forum: Desktop Environments
---

### Post by brian70809 on 2011-04-30
I have some icons in the Dash - Applications that were for running applications in Wine..  I removed Wine because I am using Crossover, but those dead links/icons are in there.

I tried to drag to trash can, hit DEL, etc..

I have done a lot of searches.. I see how to add items, but not remove..

Help!

---

### Post by mc4man on 2011-04-30
You need to remove the associated .desktop's, usually found in a ../share/applications directory
In this case maybe  look in ~/.local/share/applications

---

### Post by brian70809 on 2011-04-30
i found 2 of them in the ~/.local/share/applications

I have always wondered how to access this location through Nautilus.. is there an easy way or do I need to do it through terminal?

Figured it out after.. Thanks for the help!

---

### Post by mc4man on 2011-04-30
when in nautilus go  > Edit > Preferences > Show hidden and backup Files
(and ck. out anything else you wish in Preferences

---

