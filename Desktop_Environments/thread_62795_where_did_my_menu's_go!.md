---
title: "where did my menu's go?!"
date: 2005-09-05
forum: Desktop Environments
---

### Post by squidy37 on 2005-09-05
my system menu's have disappeared... i dont exactly knwo how i did it tho. how do i enable them again?

---

### Post by arnieboy on 2005-09-05
[QUOTE=squidy37]my system menu's have disappeared... i dont exactly knwo how i did it tho. how do i enable them again?[/QUOTE]open up a terminal and fire the following:
```
rm -rf $HOME/.gnome/apps

```log out of gnome and log back in.

---

### Post by squidy37 on 2005-09-06
i didn't explain myself clearly.. sorry

what i meant was that the three menu's for gnome on the top left of the screen are gone, and the application launcher shortcuts have slid over to the left.. somehow i completely removed those three gnome menu's.

i did try what you suggested, but it didn't work =T  i can't even log off gnome by doing System -> Logout... so i had to ctrl+alt+f1 and start X again which gave me some error about panels(?).. so i restarted and the menu's are still missing.

---

### Post by matthew on 2005-09-06
In the bar where the menus were, right click and select "Add to Panel." Then add the applet titled "Menu Bar."

---

### Post by squidy37 on 2005-09-06
thank you~! that was quite noob xP haha

---

### Post by matthew on 2005-09-06
You are welcome--glad to help. Don't be embarrassed, we all do stuff like that from time to time. Asking for help is the first step to gaining knowledge.

---

