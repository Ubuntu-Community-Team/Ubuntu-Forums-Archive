---
title: "gnome-main-menu / slab questions"
date: 2009-05-22
forum: Desktop Environments
---

### Post by WindowSmasher on 2009-05-22
I have two questions that I've been unable to answer via google or the forums:

1. In openSuse the gnome-main-menu / slab has a colored border. Can I add this to the gnome-main-menu / slab in ubuntu? As of now it has now border in ubuntu.

2. When new documents are added to the Recent Documents menu, my gnome-main-menu / slab menu increases in size. I would like to reduce the number of recent documents that the menu is permitted to hold.

Any help would be appreciated.

Thank you!

---

### Post by WindowSmasher on 2009-05-22
So I was able to place a band aid on issue number 2 by following the short guide [[COLOR="Blue"]here[/COLOR]]("http://ubuntu-snippets.blogspot.com/2009/02/recently-usedxbel-xml-horror.html") (must create .gtkrc-2.0 per instructions). Be advised, this also completely removes the Documents tab from the gnome-main-menu / slab menu if you have no favorite documents marked.

However I am still working on just limiting the number of recent documents. I have tried the gtk-recent-files-max-age option and set it to =4, but have had no luck. It seems to be all or nothing at this point.

I would still like to add a border to the gnome-main-menu / slab menu. Any advice would be appreciated.

---

### Post by wersdaluv on 2009-05-22
I'm sorry but I don't remember if and how I managed to fix that. I think, it was something like dragging the corner of the menu to make it bigger or smaller. Bigger means it will show more documents and apps. 

I don't know what you mean by border but it must have something to do with the gtk theme. You may want to try OpenSuSE's gilouche for best integration. Please upload a screenshot to show what you mean.

---

