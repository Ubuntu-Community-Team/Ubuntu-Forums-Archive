---
title: "firefox doesnt keep history in history menu"
date: 2009-01-03
forum: General Help
---

### Post by flclvr8780 on 2009-01-03
hey guys, when i go to check my history, the sidebar is blank, but when i type in the awesomebar, the typed stuff is still there as is my bookmarks.  i have keep history checked and the value greated then zero, any ideas?

---

### Post by Jack-in-Box on 2012-05-29
> **flclvr8780 said:**
> hey guys, when i go to check my history, the sidebar is blank, but when i type in the awesomebar, the typed stuff is still there as is my bookmarks.  i have keep history checked and the value greated then zero, any ideas?

I sporadically get the same irritating problem. I can restore the history from backup of the profile and at least bookmarks etc aren't lost.

---

### Post by sgage on 2012-05-29
> **flclvr8780 said:**
> hey guys, when i go to check my history, the sidebar is blank, but when i type in the awesomebar, the typed stuff is still there as is my bookmarks.  i have keep history checked and the value greated then zero, any ideas?

This typically means your places.sqlite file is corrupted. It used to happen fairly often for me, but not at all lately. You can go into your profile, delete places.sqlite, and on next run Firefox will recreate it. You will still have all your bookmarks, but lose all their favicons. And your history will start recording from that time on. 

There's an add-on called Places Maintenance that you can use to check the "sanity" of the database and do some maintenance.

---

