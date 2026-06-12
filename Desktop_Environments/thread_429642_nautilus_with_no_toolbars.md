---
title: "nautilus with no toolbars"
date: 2007-05-01
forum: Desktop Environments
---

### Post by Ozeuss on 2007-05-01
I've recently compiled nautilus to have tracker search integration. 
It works fine, the thing is- the links in the places menu open up a nautilus window but with no toolbars or side pane (and F9 does not reveal them). when i open up nautilus through the link in "accessories" it opens normally (with toolbars). 
The difference is that the launcher that opens up normally has a " --browser" operator:
 ```
nautilus --no-desktop --browser %U
```
the icons in the "Places" menu do not .
similarly, if i create a link of a folder on the desktop, it opens up the cut-down version. if i right click the icon, it shows a "Browse" option that opens up the "normal" nautilus.
well, that about it. 
am i missing a package that i should have when compiling nautilus, or any other bug?

---

### Post by mcduck on 2007-05-01
It's not a bug, and you are not missing anything. What you are seeing is Nautilus in it's default spatial mode instead of the browser mode.

If you wish Nautilus to always use browser mode just go to Edit/preferences and on the Behavior-tab enable 'Always open in browser windows' :)

---

### Post by Ozeuss on 2007-05-01
Thanks! that did the trick.
i can't believe i missed that, i tried to look both there and in gconf.. i think i actually ticked it and unticked it again in gconf...

---

