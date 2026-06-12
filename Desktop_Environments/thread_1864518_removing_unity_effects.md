---
title: "removing unity effects"
date: 2011-10-19
forum: Desktop Environments
---

### Post by davidmaxwaterman on 2011-10-19
Hi,

I switched to classic gnome desktop, but there are still some oddities that I would like to get rid of.

1) when I try to move a window around using the top menu bar, my mouse often strays into the top menu bar. this causes the window to be maximized. is there a way to remove this behaviour?

2) when I try to scroll on some windows (eg pidgin buddy list), there is no normal scroll bar. instead, something like a scroll bar pops up when I put the mouse there. unfortunately, I often move my mouse to the edge of the window when I want to widen it, which I can't do with the odd scroll bar there. it's very irritating. Is there a way to remove this scroll bar thing, so I get the normal scroll bar as before?

Perhaps I'm wrong about this being anything to do with unity, but I observed similar things when I tried it out.

Max.
11.04

---

### Post by mc4man on 2011-10-19
1. install compizconfig-settings-manager open it up & disable the grid plugin
Forget where it is in menu, maybe preferences or run ccsm

2.  That's the overlay scrollbar. To remove entirely - 
```
 sudo apt-get purge liboverlay-scrollbar*
```

Then do a log out/in

---

### Post by davidmaxwaterman on 2011-10-19
> **mc4man said:**
> 1. install compizconfig-settings-manager open it up & disable the grid plugin
Forget where it is in menu, maybe preferences or run ccsm

2.  That's the overlay scrollbar. To remove entirely - 
```
 sudo apt-get purge liboverlay-scrollbar*
```

Then do a log out/in

perfect :)

thanks!

---

