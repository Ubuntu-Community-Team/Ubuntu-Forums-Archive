---
title: "totem player is in pernament full screen"
date: 2009-04-08
forum: General Help
---

### Post by banana jama on 2009-04-08
im using ubuntu 8.10. this is a recent problem my totem player only plays files in full screen. even worse i can't minimize it once it opens. the only way i can close it is the press ctrl alt and right button then go to system---->administration--->system monitor and force close it. does anyone else have this issue and know how to solve it. 

p.s. I've tried every option totem has including resize, leave full screen, everything.

---

### Post by banana jama on 2009-04-08
I've found the solution to the problem. if anyone comes across the problem open natilus go to view and click hidden files. go to .config---totem---state.ini  and delete state.ini file. this should solve the problem it did for me.

---

### Post by neu2buntu on 2009-04-08
the only thing i can think of is to use the gconf-editor to have a look at the settings in totem ,
do code in terminal ```
gconf-editor
``` and goto >apps >totem >left click on "totem" and possibly try changing values for auto-resize and window_on_top .do this by right-click and edit key...  (mine are both unticked) and have no problems and see if it makes any difference ...if not just reverse the above procedure.

OOOPS TOOO LATE!!! at least you got it sorted

---

