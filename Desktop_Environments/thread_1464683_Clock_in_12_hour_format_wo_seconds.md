---
title: "Clock in 12 hour format w/o seconds?"
date: 2010-04-28
forum: Desktop Environments
---

### Post by vDub2000 on 2010-04-28
I don't like the idea that the clock in Xubuntu uses military time rather than the 12 hour format. Is there a way to change it so that it uses the 12 hour format w/o showing the seconds?

---

### Post by sisco311 on 2010-04-28
Right Click -> Properties -> select *Custom* from the *Clock Options*, paste:
```
%l:%M %p
```in the text box.

EDIT: for a list of format options open a terminal (Applications -> Accessories -> Terminal) and run:
```
man date | less +/"FORMAT controls"
```
use the arrow keys to scroll down/up the page, press q to quit.

---

