---
title: "Compiz doesn't work properly"
date: 2008-12-07
forum: General Help
---

### Post by Pazau on 2008-12-07
Hello everyone.

I have a Hp dv6645eo with Linux Ubuntu 8.10 on.

Specs: [http://h10025.www1.hp.com/ewfrf/wc/d...reg_R1002_USEN](http://h10025.www1.hp.com/ewfrf/wc/d...reg_R1002_USEN)

Now I have so got it mostly to work - apart from the delicious effects.
When I turn on effects, so they work well enough, but the title bar of each window becomes white when the mouse crosses them. I can not even see the three buttons on each window.

My graphics card is from Nvidia and the driver is the latest - version 177.
Although I chose driver version 173, so the problem is the same, so I do not think it is the driver there is something wrong with.

What can the problem is due and how do I remedy this?

---

### Post by Wartender on 2008-12-07
maybe ```
metacity --replace
```? see if that works

---

### Post by Pazau on 2008-12-15
The problem was that there had not been any dot inside the system -> Preferences -> Appearance. When I put a dot in the lower option (maximum effect) so it seemed as it should. :)

---

