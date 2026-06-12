---
title: "Background of gedit-window becomes a screenshot"
date: 2019-08-17
forum: Desktop Environments
---

### Post by belanchuk on 2019-08-17
When starting gedit from an ordinary user, the background of his window becomes a screenshot.
It doesn't sound clear, so please watch the animated gifs. You can pause animation on imgur.com.

[https://imgur.com/gallery/w8aDa1O](https://imgur.com/gallery/w8aDa1O)

[[IMG]https://img16.lostpic.net/2019/08/16/6dafc2d2a67fa159746500a397ca6683.th.gif[/IMG]]("https://img16.lostpic.net/2019/08/16/6dafc2d2a67fa159746500a397ca6683.gif")


But when I run gedit from root, everything works correctly.
I noticed this problem not only with gedit, but also with dbeaver.

---

### Post by belanchuk on 2019-08-17
Solved the problem by deleting the line "run_im xim" in ~/.xinputrc

---

