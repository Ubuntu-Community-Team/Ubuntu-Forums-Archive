---
title: "Help! My theme doesn't change"
date: 2010-07-08
forum: Desktop Environments
---

### Post by KingArthur72076 on 2010-07-08
I am trying to use Emerald Theme Manager and I have downloaded a theme, imported it and it's showing there but it won't change on the desktop.

I have tried double clicking the theme...pressing enter while its highed...nothing changes. What am I doing wrong?

---

### Post by KingArthur72076 on 2010-07-09
Can anyone tell me how to get this to work?

---

### Post by stinkeye on 2010-07-09
Hit alt+F2
```
emerald --replace
```click run



to revert```
gtk-window-decorator --replace
```


If your using compiz, install fusion-icon to easily change between window decorators.
In the terminal
```
sudo apt-get install fusion-icon
```
Once installed, you will find it in system tools.

---

### Post by KingArthur72076 on 2010-07-09
Thank you... "emerald --replace" worked. Also thanks for the other info too. Still learning....

---

