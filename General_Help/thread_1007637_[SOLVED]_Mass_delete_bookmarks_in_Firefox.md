---
title: "[SOLVED] Mass delete bookmarks in Firefox"
date: 2008-12-10
forum: General Help
---

### Post by jimbob on 2008-12-10
I need to delete all entries in my bookmarks list in Firefox so I can roll in a new one.

When I put a new one in, it just adds itself to the tail of the existing one even though many entries are identical.

How do I "select all" in the bookmarks list so I can mass delete the entire thing?

---

### Post by jimbob on 2008-12-14
bump

---

### Post by kspringer on 2008-12-14
If I understand you correctly, from the Firefox menus, try "Bookmarks/Organize Bookmarks" and delete the ones you want deleted?

Hope that helps.

k

---

### Post by jimbob on 2008-12-14
Thanks, but that is a long point and click operation on each entry and is a PITA if you have a long file like I do.

I want to delete ALL the old bookmarks at once before loading a new bookmarks.html file.

---

### Post by kspringer on 2008-12-14
EDIT:  If you do the "Bookmarks/Organize Bookmarks" bit, and select ONE bookmark -- if you hit Ctrl-A, it'll select all bookmarks.  You can delete all of them at one time.

If that doesn't work, you can do the below:  STOP EDIT.


Try deleting the entire bookmarks file, then.  I use Kubuntu so my Firefox bookmarks file is under:

~/.mozilla/firefox/<random-letters like wzfxk26s>.default/bookmarks.html

There's a bookmarksbackup subdirectory in this directory so if it goes REAL bad, you can restore.




k

---

### Post by jimbob on 2008-12-14
Thanks a million - your CTRL-A works great!:p

EDIT:  This is the solution that Mozilla came up with -

> Start Firefox in safe mode, in the first dialog that pops up, select "Reset bookmarks to Firefox defaults" then click "Make changes and Restart"
You will left with a small number of default bookmarks. 

I like yours better because I don't end up with any "default" bookmarks which I have to also delete anyway.

---

