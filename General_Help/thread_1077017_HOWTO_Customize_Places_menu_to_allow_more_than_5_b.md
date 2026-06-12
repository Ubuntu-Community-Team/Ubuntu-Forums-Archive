---
title: "HOWTO: Customize Places menu to allow more than 5 bookmarks"
date: 2009-02-21
forum: General Help
---

### Post by schnauzer93 on 2009-02-21
[http://linux.blogs2k.com/2009/02/21/howto-display-more-than-5-bookmarks-in-gnome-panel-places-menu/](http://linux.blogs2k.com/2009/02/21/howto-display-more-than-5-bookmarks-in-gnome-panel-places-menu/)

Am I the only one who thinks this should be stored in a configuration file somewhere?

EDIT: Suggestion: Instead of changing the line > if (g_slist_length (add_bookmarks) <= MAX_ITEMS_OR_SUBMENU) { 

why not just change the line > #define MAX_ITEMS_OR_SUBMENU    5 to whatever you want? But that's just me.

---

