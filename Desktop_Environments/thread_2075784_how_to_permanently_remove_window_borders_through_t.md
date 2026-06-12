---
title: "how to permanently remove window borders through terminal?"
date: 2012-10-24
forum: Desktop Environments
---

### Post by tertian on 2012-10-24
Well, what the title says. I don't wanna use ccsm, cause the last time i did, it was really buggy and changing simple things wouldn't work, or it would destroy the whole system and make it unusable. I don't even have it installed since 11.04 i think

I'm only asking cause i use easystroke (mouse gestures) and perform all actions through the mouse, so it really is unnecessary to have window borders and i just realized because something probably crashed and they went away.

---

### Post by pqwoerituytrueiwoq on 2012-10-24
why would you want to do that?
these commands should do it, but it does not work for me
```
gconftool-2 -s -t string /apps/compiz-1/plugins/decor/screen0/options/shadow_match none
gconftool-2 -s -t string /apps/compiz-1/plugins/decor/screen0/options/decoration_match none

```
this is where to go in [ccsm](apt:compizconfig-settings-manager)
[[img]http://www.zimagez.com/miniature/screenshot-10242012-020542pm.php[/img]](http://www.zimagez.com/zimage/screenshot-10242012-020542pm.php)

---

