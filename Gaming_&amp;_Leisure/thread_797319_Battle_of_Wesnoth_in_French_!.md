---
title: "Battle of Wesnoth in French ?!"
date: 2008-05-17
forum: Gaming &amp; Leisure
---

### Post by sploutch on 2008-05-17
Hi!

How can I have Battle of Wesnoth in French on my Ubuntu (in English by default)?

I've installed the "wesnoth-all" package and the game is playing very well, but in English. And when I try to choose another language on the configuration's menu, there is no effect... Always in English!!!

Please, help me...

Sploutch.

---

### Post by dudeofthedead on 2008-05-17
The only possible explanation I can think of is you're not allowed to do that in-game.  There's probably some config file lying around in your home folder, inside a directory starting with '.' (ex: .wesnoth), which by default will make it invisible.

---

### Post by sploutch on 2008-05-18
Okay guys, I found the solution by myself... I just install both packages below:

```
sudo aptitude install language-pack-fr language-pack-fr-base
```

And that's it!!!  :)
See ya!

---

