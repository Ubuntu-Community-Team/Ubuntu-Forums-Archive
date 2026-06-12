---
title: "Installed programs don't appear in Kmenu"
date: 2006-04-20
forum: Desktop Environments
---

### Post by Big.Nikito on 2006-04-20
I've recently installed firefox and thunderbird with the aptitude command. But their items don't appear in the kmenu. When I try to create an item manually, I get no error message but still my changes never take effect. This problem is new, because I have installed a firefox item without any problems several weeks ago. Now I'm not even able to delete this item. It seems that I can't make any changes at all. I hope somebody can help me.

---

### Post by aysiu on 2006-04-20
It sounds as if your KDE profile has somehow become corrupted. If you don't mind losing some of your other preferences, you can try this:

1. Log out
2. Press Control-Alt-F1
3. Log in
4. Type ```
mv ~/.kde ~/.kde_old
```
5. Log out
6. Press Control-Alt-F7
7. Log in again
8. Try to add Firefox to the KMenu

---

### Post by Big.Nikito on 2006-04-20
I tried that but still can't change the kmenu. And I tried to do it with kappfinder, no changes. And I have an other problem too. If I log out I don't get the log in screen but my monitor goes to sleep mode. Could it be that those problems are somehow  related?

---

### Post by Neo Ex on 2006-04-20
Try running 'kbuildsycoca' from a terminal to update the menu.

---

