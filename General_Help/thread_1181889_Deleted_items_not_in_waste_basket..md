---
title: "Deleted items not in waste basket."
date: 2009-06-08
forum: General Help
---

### Post by al688 on 2009-06-08
I have just done a fresh install of jaunty 64.  Everything works fine other than when I delete an item it does not appear in the waste basket.  If I hover over the basket it tells me that the basket is empty.  When I open it there are no items visible.  The deleted items are going somewhere but not to the waste basket! 
Any ideas as I'm now reluctant to delete anything just in case I need it?

---

### Post by michy99 on 2009-06-08
1. What method are you using to delete? Press delete button or right click and select Move to Trash?

2. Are you deleting as a regular user or as root?

---

### Post by Vunutus on 2009-06-08
Open up gconf-editor, expand the "apps" folder, then scroll down to "nautilus", expand it, and click on "preferences". Look in the list of options that appears for "enable_delete" and make sure the box is unchecked. If it's checked, deleted files will bypass the trash can as you described.

---

### Post by al688 on 2009-06-08
Thanks for the replies.  I usually right click to delete items.  I have not been deleting them as root.  I have checked the settings and the box is unchecked.

---

### Post by al688 on 2009-06-08
Tried restarting the system and the problem appears to have rectified itself.  From looking at other posts/sites it appears there is a bug in 9.04 that can cause this problem.

---

