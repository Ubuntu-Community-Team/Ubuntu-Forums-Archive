---
title: "Tooltips/mouseover boxes are blank"
date: 2011-04-20
forum: Desktop Environments
---

### Post by oohyeah on 2011-04-20
This happens mainly with Eclipse, where I hover over a variable and a tooltip box appears, but I cannot read anything in the box because it is either all white or all black.  A similar, but not identical, issue occurs in Skype where I open a drop down menu and the menu is all black except when I mouse over where the items might be -- then the item appears for as long as the cursor is over it.

---

### Post by Copper Bezel on 2011-04-20
It sounds like the application is using your tooltip background color but specifying a foreground (text) color. For Skype, make certain you've set your Appearance in its General settings to GTK+. I don't know Eclipse, so I can't really help there.

---

### Post by Krytarik on 2011-04-20
+1 for Skype

Regarding Eclipse, please see this earlier post:
[http://ubuntuforums.org/showthread.php?p=10432727#post10432727](http://ubuntuforums.org/showthread.php?p=10432727#post10432727)

Hope it helps!

---

### Post by oohyeah on 2011-04-20
Excellent!  The appearance settings were the issue.  Thanks for your help, Copper and Krytarik.

---

