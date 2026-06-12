---
title: "How to remove y-axis winodw restrictions"
date: 2009-05-30
forum: General Help
---

### Post by falcon1620 on 2009-05-30
I am having a problem with 9.04 where it restricts my windows from going past the top window bar on the screen, since I'm on an eee-pc 701, this is a real annoyance because I can not move windows around on the tiny screen to click on things like apply and ok (using alt click). This was not an issue with 8.10, please how do I remove the y-axis restriction. I can't find this info anywhere.

---

### Post by Hobgoblin on 2009-05-30
[From here](https://help.ubuntu.com/community/EeePC/Using)

> gconftool-2 --set /apps/compiz/plugins/move/allscreens/options/constrain_y --type bool 0

---

### Post by falcon1620 on 2009-05-30
O thanks. I got it ;) I could not get this working for some reason, it is working now. I fatfingered it.

---

