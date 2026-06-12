---
title: "Please help! Compiz totally outtta WHACK!"
date: 2008-12-12
forum: General Help
---

### Post by Zanzik on 2008-12-12
I've installed Ubuntu 8.10 at least 3 times before now. Yesterday, I decided to run a complete re-install, as I have done successfully many times before, and for some reason had a lot of problems. I know that the problem stems from compiz, because when I install it and set it up, as I was always able to, the screen turns black and anything I click turns black too. The only way to stop it is by remembering where the terminal is, and typing "pkill compiz" which immediately solves the problem. But THEN, I have no window titlebars, in fact, I can't switch desktops, switch windows, move a window, or even see it in the bottom bar. I can't do anything with compiz and just about everything I set causes it to glitch again. This has NEVER happened to me before, I don't know what I've been doing differently but any support on this would be extremely helpful.

---

### Post by SmokinJuan on 2008-12-13
rather than typing "pkill compiz", type

```
metacity --replace
```

---

