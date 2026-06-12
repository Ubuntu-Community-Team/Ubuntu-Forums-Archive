---
title: "How to get back my wastebasket"
date: 2010-01-05
forum: Desktop Environments
---

### Post by Lavix on 2010-01-05
I accidentally removed the wastebasket from the bottom panel right corner. Is it possible to get it back at the same place. I tried to use a right-click on the bottom panel and got it back, but it is not on the same place any more, even after moving it. Any idea? Thanks.

---

### Post by zine92 on 2010-01-05
You mean you had already "add to panel" the trash already. Which left with moving. Try unlocking the workspace switcher and try moving again. Sometimes is because it is lock therefore making it impossible to move. Hope that helps.

---

### Post by Lavix on 2010-01-05
I found how to do that. From your home folder in the terminal type the below commands:
```

rm -rfd .gnome .gnome2 .gconf .gconfd .metacity

```
Then log off and log on to validate the original Gnome Desktop settings

---

### Post by mbeach on 2010-01-05
I would say zine92's solution would be the better way to go. Your solution may have adverse effects for a number of other programs and I'd caution any future readers to make a back up of those directories prior to removing them.

---

