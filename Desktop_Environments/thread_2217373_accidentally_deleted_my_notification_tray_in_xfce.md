---
title: "accidentally deleted my notification tray in xfce"
date: 2014-04-17
forum: Desktop Environments
---

### Post by grier-devon on 2014-04-17
So I accidentally remove my notification tray. I try going to panel>add new items but the "notification tray" is grayed out so it won't let me add. Thanks for any help. I am using Xubuntu 14.04.

---

### Post by Toz on 2014-04-17
If its greyed out, it means it must still be on a panel somewhere. How many panels do you have? Have you checked the Items tab for each panel that you have to see if its there? Can you also open a terminal window, run the following command and post back the results:
```
xfconf-query -c xfce4-panel -lv
```
...this might help to identify where it is.

---

