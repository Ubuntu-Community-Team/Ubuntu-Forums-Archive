---
title: "GNOME vertical maximize keyboard shortcut"
date: 2008-06-07
forum: Desktop Environments
---

### Post by indil on 2008-06-07
I bind the left Windows button to the GNOME keyboard shortcut that vertically maximizes the currently selected window.  Before Hardy, pressing the button twice would return the window to its original dimensions.  Now, the window remains vertically maximized.  Does anyone else have this problem or know how to get it to work the way I like?

---

### Post by mody on 2008-06-20
Works for me. Are you sure you bind the key to the correct action? I use both "Maximize window vertically" and "Maximize window horizontally" since Gnome started using Metacity and it toggles.

---

### Post by mody on 2008-06-23
I might found the solution. Toggle key-bindings for metacity don't work with compiz enabled. You have to change the bindings using gconf-editor in /apps/compiz/general/allscreens/options/

toggle_window_maximized_vertically_key and toggle_window_maximized_horizontally_key

HTH
Patrik

---

### Post by indil on 2008-07-02
I set the values for "maximize_window_vertically_key" and "toggle_window_maximized_vertically_key" to "Super L" but nothing changed.  I tried restarting X but it made no difference.

---

