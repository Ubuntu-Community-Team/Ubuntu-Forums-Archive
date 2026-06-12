---
title: "Compiz + Mouse Pointers"
date: 2009-07-14
forum: Desktop Environments
---

### Post by msgmikeh on 2009-07-14
Currently, I am experiencing a small issue with mouse pointers, while Compiz is running. I change the pointer theme in appearance, and the pointers change inside windows that are not system related (ie: Firefox). 

But, the overall pointer theme does not change. I can turn off Compiz and the pointers change system wide. 

I found this thread on the issue:
[http://ubuntuforums.org/showthread.php?t=620380](http://ubuntuforums.org/showthread.php?t=620380)

I have CCSM installed, but I am missing the "cursor theme" option in the general settings section. I think I am running 0.8.2.

---

### Post by msgmikeh on 2009-07-14
I found two bug reports about the issue, but I'm not real sure how to implement the fix:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/141500](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/141500)
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/86184](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/86184)

Could anyone lend a hand? Thanks!

Oh, and I'm running 9.04.

---

### Post by Toadinator on 2009-07-15
I have the exact same issue! Also, grouping/tabbing windows is missing! How come compiz was working just fine on 8.10 but its suddenly broken on 9.04? I even re-installed and I still have the same problem X_X.

---

### Post by red_spyder on 2009-09-04
I have actually had the same problem, where the mouse theme would work on firefox and other non-ubuntu programs alone. I fixed my problem by opening a terminal and typing:
```
gtk-window-decorator --replace
```
like another thread had said, then I logged off and logged back on. I'm not sure which one of these fixed the problem or if both did, but I guess someone can try each out.

---

