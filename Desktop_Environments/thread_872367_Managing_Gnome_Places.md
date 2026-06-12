---
title: "Managing Gnome Places"
date: 2008-07-27
forum: Desktop Environments
---

### Post by navaburo on 2008-07-27
I have added several entries to the Gnome Places as bookmarks using the "connect to server..." dialog. However, some are extraneous, and I wish to delete them. However, right clicking on the entries opens them rather than allowing me to configure them. This is either a bug or poor design, imo.

I made an entry called Arrakis, then using
```
cat `find ~ | grep xml` | grep -i Arrakis
```
I searched for it. However the search returned no results.

---

### Post by softtower on 2008-07-27
1. Open Nautilus window with (for instance) "Places" -> "Home Folder" in the main Gnome menu.
2. Do "Edit Bookmarks" via Ctrl+B or "Bookmarks/Edit Bookmarks" menu.

---

