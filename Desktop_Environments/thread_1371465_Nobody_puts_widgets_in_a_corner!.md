---
title: "Nobody puts widgets in a corner!"
date: 2010-01-03
forum: Desktop Environments
---

### Post by noah++ on 2010-01-03
Hi,

I want to center a Bubblemon widget above my taskbar clock, the lower-right corner of my desktop. But when I position it that way, it moves itself away from the edge of the screen, toward the center of the desktop. When I have my timer widget in the same area, Bubblemon drags it along too.

I can understand the benefits of this behavior, but I still don't want it. Can I make it stop?

---

### Post by benerivo on 2010-01-03
I think there is a some sort of zone around each plasmoid that keeps them apart from each other. I had this happen to me, but it only happened when i had the desktop set to the 'Desktop Acitivity' set to 'Desktop' (the default setting). Once i changed it to 'Folder View' then it stopped shifting the plasmoids and i could have them overlapping and positioned partially off screen.

---

### Post by lovinglinux on 2010-01-03
I can overlap widgets using both "Desktop View" and "Folder View". Perhaps is because I use Compiz instead of Kwin.

BTW, when I added Bubblemon, it changed the size of another widget already on the screen. So perhaps Bubblemon is the culprit.

---

### Post by benerivo on 2010-01-03
lovinglinux, i also use compiz, and can actually overlap plasmoids (in direct contradiction to what i've said above!), but they are moved away from each other in particular cases. In Desktop View try adding two folder view plasmoids and move one in to a corner so that it is slightly off-screen. Does it jump back so it is completely on screen? Then move the second folder view so that it overlaps the edge of the first, and is also slightly off-screen. Does it jump back, and also move the first to a slightly different position?

Hey, 1,000 posts. Over half of them were bad advice but what the hell!

---

### Post by noah++ on 2010-01-03
Thanks. Changing to Folder View did eliminate the problem. But I'd prefer to use the normal view. And in the normal view, all of my widgets want some padding, just some more than others. Bubblemon seems particularly greedy.

---

### Post by lovinglinux on 2010-01-03
> **benerivo said:**
> lovinglinux, i also use compiz, and can actually overlap plasmoids (in direct contradiction to what i've said above!), but they are moved away from each other in particular cases. In Desktop View try adding two folder view plasmoids and move one in to a corner so that it is slightly off-screen. Does it jump back so it is completely on screen? Then move the second folder view so that it overlaps the edge of the first, and is also slightly off-screen. Does it jump back, and also move the first to a slightly different position?

Yep, it jumps back. But not in Folder view.

---

### Post by benerivo on 2010-01-03
It may have something to do with the plasma theme you are using. If you want to you could try changing the theme to see if it changes this 'buffer distance'. Otherwise, i've never seen any configuration for the plasma workspace so i'm not sure there is much that can be done about it.

---

