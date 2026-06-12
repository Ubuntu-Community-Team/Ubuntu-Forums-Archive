---
title: "some games wont run"
date: 2007-04-14
forum: Gaming &amp; Leisure
---

### Post by dr.silly on 2007-04-14
my screen just flashes and nothing else happens

---

### Post by Bekker on 2007-04-14
Can you be 'a bit more' specific?
I'm guessing it has to do with you 3d-card, so you should get the flashes when trying to play games that require 3d-acceleration.

Try this in a terminal:
```
glxinfo | grep direct
```
output should give you "direct rendering: Yes" if you want to be able to play 3d games.

---

### Post by dr.silly on 2007-04-14
even supertux it isn't the 3d

---

### Post by Bekker on 2007-04-14
Although the game doesn't look like it's using any 3d-acceleration doesn't mean it doesn't need it. On happypenguin.org it says it does require 3d-acceleration.

To be sure you can run supertux from the commandline and see if it gives you some output on what causes the error.

---

