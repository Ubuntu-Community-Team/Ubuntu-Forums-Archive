---
title: "Is there a way to adjust scroll wheel sensitivity?"
date: 2006-06-05
forum: Desktop Environments
---

### Post by darthvivi on 2006-06-05
Just curious. If it were possible I would probably like to tweak it a little bit.

---

### Post by jlintz on 2006-06-13
i'd also really like to know how as well

---

### Post by keke21 on 2006-06-13
Same. Out of everything, I like the mouse options the least. Ubuntu detected every special key on my keyboard and mapped them correctly, but my mouse is pretty blank.

---

### Post by shakin on 2006-06-13
Try these options in xorg.conf in the mouse device section. Adjust as necessary.

> 
Option        "VertScrollDelta" "250"
Option        "MinSpeed"      "0.06"
Option        "MaxSpeed"      "0.12"
Option        "AccelFactor" "0.0010"


It's possible these don't work with all mouse drivers. They might just be called something else for your mouse.

---

