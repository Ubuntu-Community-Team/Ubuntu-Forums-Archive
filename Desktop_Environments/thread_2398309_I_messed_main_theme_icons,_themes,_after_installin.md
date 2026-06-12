---
title: "I messed main theme icons, themes, after installing &amp; trying some new themes"
date: 2018-08-10
forum: Desktop Environments
---

### Post by MariosFFX on 2018-08-10
Hello.
As the topic says I messed up pretty badly main Adwaita theme
How can  I fix it back?

[https://s26.postimg.cc/k4aco7usp/Screenshot_from_2018-08-10_10-37-56.png](https://s26.postimg.cc/k4aco7usp/Screenshot_from_2018-08-10_10-37-56.png)

---

### Post by deadflowr on 2018-08-10
Try
```
dconf reset -f /org/gnome/desktop/interface/
```

Edited: I forgot the recursive flag -f

---

### Post by MariosFFX on 2018-08-11
Didn't work.
Maybe I should reformat.

---

### Post by deadflowr on 2018-08-11
How about trying to reinstall the adwaita-icon-theme package.
Or (a better question would be)
What where you playing around with to mess up the icons in the first place?

I'm not sure a reformat reinstall and going nuclear is needed as something like this should be reversible. (fixable)

---

