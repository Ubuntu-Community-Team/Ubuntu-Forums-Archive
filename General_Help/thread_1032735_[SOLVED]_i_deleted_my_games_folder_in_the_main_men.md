---
title: "[SOLVED] i deleted my games folder in the main menu!"
date: 2009-01-06
forum: General Help
---

### Post by helpineed on 2009-01-06
Ok, I was trying to create a Wine folder in main menu (I had also deleted that) and then I realized that the games folder had somehow been deleted. Is there another way to get my Games folder back apart from creating it by scratch (I already tried it).

---

### Post by blazemore on 2009-01-06
Can't you right-click and do Edit Menus?

---

### Post by eatberrys on 2009-01-06
click system->prefrences->"main menu" u should be able to slect what u want viewable on the main menu.

---

### Post by donkyhotay on 2009-01-06
> **eatberrys said:**
> click system->prefrences->"main menu" u should be able to slect what u want viewable on the main menu.

This only works if he has just unchecked the games menu. If it's deleted entirely I don't know of any way of recovering it.

---

### Post by eatberrys on 2009-01-06
Theres always computer data recovery ;) but its not worth it for that.

---

### Post by blazemore on 2009-01-06
Have you tried System -> Preferences -> Main Menu -> Revert?

Failing that, a simple
```
sudo debconf gnome-panel
```
Should be what you need.

---

### Post by helpineed on 2009-01-06
uh a mixture of the last two methods:

first i did the code and two new bars appeared with default settings
then i reverted my old one and deleted the new ones

i got my games folder back
and my wine folder

---

### Post by blazemore on 2009-01-06
So if the issue is solved, say what solved it, and set this thread to SOLVED.
Thanks

---

### Post by helpineed on 2009-01-06
um, how do i set it to solved?

---

### Post by Sef on 2009-01-06
At the top, under thread tools > Mark as solved.  (I set it for you.)  Thank you for asking how to do that.

---

