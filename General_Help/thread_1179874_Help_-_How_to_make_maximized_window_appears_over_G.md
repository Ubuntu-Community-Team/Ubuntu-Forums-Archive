---
title: "Help - How to make maximized window appears over Gnome panel?"
date: 2009-06-06
forum: General Help
---

### Post by netlaptop on 2009-06-06
A maximized window appears over the panel may make me feel that I am getting more "space" to work with the opening window and more easier to concentrate:p

So, can we make a maximized window appears over the Gnome panel which is located on the top?

For example, when we click on the maximize button of Firefox, the he maximized window should appears over the panel (like pressing F11 > Fullscreen for Firefox). 


Thanks

---

### Post by plucky on 2009-06-06
You could **Autohide** the panel.Right click on panel and select **Properties** and tick the "autohide" box.


Good Luck

---

### Post by Legace on 2009-06-06
> **plucky said:**
> You could **Autohide** the panel.Right click on panel and select **Properties** and tick the "autohide" box.

+1

You might also want to open **gconf-editor** and browse to:
/apps/panel/toplevels/bottom_panel_screen0
and
/apps/panel/toplevels/top_panel_screen0

make sure the values are setup something like this:
auto_hide_size = 1
hide_delay = 0
unhide_delay = 0

---

### Post by netlaptop on 2009-06-06
Thank you so much!

---

### Post by jbruced on 2009-06-06
I used keyboard shortcuts.

Set F11 under window section to toggle fullscreen, I didn't know before that you could fullscreen most other windows just like ff.

---

