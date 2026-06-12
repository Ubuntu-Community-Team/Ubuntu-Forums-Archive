---
title: "Attaching Programs to the side."
date: 2009-01-21
forum: General Help
---

### Post by Atrus6 on 2009-01-21
I tried googling it, but I wasn't sure of the correct term, I tried docking, sidebar etc, but came up with unrelated items.

What I'm trying to do is have pidgin on the right side, stuck to the side.  That way if I maximize something (like firefox), it doesn't cover up the pidgin friends list.

Latest Ubuntu, and Gnome

---

### Post by gettinoriginal on 2009-01-21
The term you are looking for is "always on top", which I do not find an option for on Pidgin.  But you can try googling for that.  :p

---

### Post by Atrus6 on 2009-01-21
Not really, unless you are not referring to the option that you get by right-clicking on a windows titlebar.

It does put it always on top, but, if I maximize something else, the right side is covered by pidgin.  I want it to maximize UP TO pidgin.

---

### Post by zhocchao on 2009-01-21
hi 
I can offer you some workaround as I had a similar problem.
(wmctrl must be installed. wmctrl does not work with minimized/maximized windows this way)

wmctrl -r :ACTIVE: -e "0,0,0,1268,745" 


width and height must be replaced with your values, so it fits your desktop-pidgin window.
I am using easystroke and xbindkeys. Also you could create a starter in a panel. It's not real maximizing, but I did not find a better solution.
g
z

---

