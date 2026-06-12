---
title: "KDE black screen after login"
date: 2018-02-20
forum: Desktop Environments
---

### Post by epeedk on 2018-02-20
I am running Kubuntu 17.10.

When I log in, it starts up normal, and for a split second shows my normal desktop backgrounds, but before anything else is displayed everything goes black, and only the mouse pointer is visible.

I am able to press ALT + F2 and get the top search menu, and start programs, but the normal menu line is absent, and everything else about the normal desktop is missing.

Any clue about what to do besides a complete reinstall?

---

### Post by epeedk on 2018-02-20
I tried to reinstall, and everything went back to normal until after I updated and changed the background image on one screen (dual screen setup), then the screen with the new image is black, and i get no mouse pop-up menu.

---

### Post by Skaperen on 2018-02-21
*just guessing:*  that image file has some error when trying to load it.  if you test it and it works, that could be because different programs are loading it.  if you can load/view it ok, then try saving a new copy and use that (keep the original file somewhere else).  if it can't be displayed it might have bad contents or it might have bad permissions (_sudo chmod 444 fullfilename_ ... should make it readable by everyome).

---

