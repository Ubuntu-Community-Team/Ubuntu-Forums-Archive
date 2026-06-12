---
title: "Editing menus doesn't work, no debian bar (gnome)"
date: 2008-03-19
forum: Desktop Environments
---

### Post by apokkalyps on 2008-03-19
I notice some programs I install don't go into my gnome menus.  What causes this?

There is a section specificly for this in the "How to install ANYTHING in Ubuntu" sticky thread, and it says to add the debian bar which has pretty muchly everything.  
I have added the packages, and its installed but it doesnt show up.

When I right click and do 'edit menus', I get lists of the menus, and the debian bar's 'show' box is unchecked.  So I check it.  But there is no apply button in the window.  And when I close the window, the debian bar is still not in the Applications menu.  Then when I edit menus again, the box is unchecked again.  Actually after the box is checked, going someone else on the tree view and coming back is sufficient to reset the checkbox.  Also I have added links manually, that after a strangely long lag of time, they DID show up in the edit menu list and are checked, but it doesnt seem like its even synchronized to my actual menu because they arent listed.

Can anyone make sense of this?

---

### Post by mcduck on 2008-03-20
After installing the Debian menu you need to run 'sudo update-menus' to populate it. Then it should work, if not, try logging out and back again.

---

### Post by apokkalyps on 2008-03-20
hmm ok that sounds promising, except, i dont have an update-menus command.  I tried searching synaptic for update-menus but got nothing.
What does this mean?

---

### Post by mcduck on 2008-03-20
> **apokkalyps said:**
> hmm ok that sounds promising, except, i dont have an update-menus command.  I tried searching synaptic for update-menus but got nothing.
What does this mean?

It should be included in the 'menu' package that also contains the Debian menu.

---

