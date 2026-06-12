---
title: "Panels on the sides"
date: 2006-10-18
forum: Desktop Environments
---

### Post by BombDiggity on 2006-10-18
Hey, I would like to know if there is a way to lock the panels to the side of the computer so when I click the arrows to bring them out they only extend as far as the last icon on either the right or the left side of the screen.  Thanks guys

---

### Post by mcduck on 2006-10-18
sure. just unselect 'Extend' in the panel's options, and then select 'Show Hide Buttons'. Move your panels where you want them and that's it.

If you want to lock them to their places so that you can't accidentally move them around open Configuration Editor (applications/system tools/configuration editor or 'gconf-editor' from a terminal), browse to apps/panel/global and mark the 'locked_down' key.

This will lock all panels and panel items in their current places (and settings), so if you want to change anything you have to unmark this from gconf-editor first.

---

### Post by BombDiggity on 2006-10-18
never new about configuration editor, I'll play around a bit with it.  Thanks for the response.  Any idea how I go about locking the panels now to the side of the screen and when I click the arrow to not have them come down to the middle bottom of the screen, but to just extend on the side?

---

### Post by mcduck on 2006-10-18
> **BombDiggity said:**
> never new about configuration editor, I'll play around a bit with it.  Thanks for the response.  Any idea how I go about locking the panels now to the side of the screen and when I click the arrow to not have them come down to the middle bottom of the screen, but to just extend on the side?

Do you mean like in the pic attached?

---

### Post by BombDiggity on 2006-10-18
Oh yes!  my god yes!

---

### Post by mcduck on 2006-10-18
> **BombDiggity said:**
> Oh yes!  my god yes!
ok, the settings are visible in the pic.. but in short, the point is that the panel orientation must be set for 'top' or 'bottom' to make it extend horizontally. Then just move it to right place and lock the panels :)

---

### Post by BombDiggity on 2006-10-18
thank you very very much, that worked perfectly.  this is so much better.  Thanks again!

---

