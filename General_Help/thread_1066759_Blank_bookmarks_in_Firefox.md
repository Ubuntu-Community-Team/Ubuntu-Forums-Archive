---
title: "Blank bookmarks in Firefox"
date: 2009-02-11
forum: General Help
---

### Post by antisho on 2009-02-11
Whenever I use Firefox 3, the bookmarks toolbar and menu appear normally with all bookmarks, but the bookmarks sidebar is entirely empty and Customize has History, Tags, and All Bookmarks (empty). Restoring from backup doesn't help, and exporting to HTML doesn't work. Google is more unhelpful than usual. This also happens in Windows, so I think it's an application or maybe configuration problem. Can anyone help?

---

### Post by x33a on 2009-02-11
try creating a new profile and see if the problem persists.


open a terminal and type firefox -ProfileManager, and create a new profile.

---

### Post by antisho on 2009-02-12
Bookmarks were fine in the new profile, but it gave me the idea to try copying some files over. It seemed that the same file (places.sqlite) with all the bookmarks was also causing the problem, but after a little bashing with SQLite manager the problem is now fixed (the bookmarks table was missing a few records). Thanks.

---

### Post by x33a on 2009-02-12
i suggest that you install FEBE. it's a really useful addon, and even if your profile goes corrupt, you can easily restore it from the backups.

[https://addons.mozilla.org/en-US/firefox/addon/2109](https://addons.mozilla.org/en-US/firefox/addon/2109)

---

