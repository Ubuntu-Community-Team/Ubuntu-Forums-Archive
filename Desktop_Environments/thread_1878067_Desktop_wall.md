---
title: "Desktop wall"
date: 2011-11-09
forum: Desktop Environments
---

### Post by mbbuntu on 2011-11-09
Is it possible in ubuntu 11.04 unity to change 2*2 desktop to 3*1? The second issue is that when I move window to out of screen then same window is visible in second desktop. I don't want that.

---

### Post by pounsg on 2011-11-09
install compizconfig-settings-manager :
```
sudo apt-get install compizconfig-settings-manager
```start it :
```
ccsm
```go to general options -> desktop size
and choose 1 in horizontal  and 3 in vertical or any other combinaison that fits your need.
regards

---

### Post by arubislander on 2011-11-09
And regarding your second question, I don't think what you want is possible. Moving a window of screen on one workspace automatically moves it on to the adjacent workspace. Otherwise it would be possible to completely loose a window.

---

