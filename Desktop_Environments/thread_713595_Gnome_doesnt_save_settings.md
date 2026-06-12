---
title: "Gnome doesnt save settings"
date: 2008-03-02
forum: Desktop Environments
---

### Post by adrynalyne on 2008-03-02
Whenever I go to System, Preferences, Sessions, I cannot remove any autostart items, nor add them.

When I do, they are immediately re-enabled next boot, undeleted, and any autostart items I have created are deleted.

I've even played with the session saving options, to no avail.  I'm assuming a permission problem somewhere, but where?

I've done some searching and not found a solution yet. :(

---

### Post by adrynalyne on 2008-03-03
I sincerely apologize if bumping threads is frowned on here, but I really have no idea on how to fix this.  :(

---

### Post by adrynalyne on 2008-03-04
Being that nobody knows the answer here, I figured it out.  I will post it here in case it happens to someone else.  My ~.config/autostart file was hidden from view, even when showing hidden files.  Using nano, I found it was full of screenlets info, and marked as read only plus I had no permissions to edit it.  So I nuked it, it rebuilt on logout/in, and here I am with working settings again.

---

