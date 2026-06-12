---
title: "Metacity Window Moving and Resizing"
date: 2009-03-10
forum: Desktop Environments
---

### Post by Temik on 2009-03-10
I'm using ubuntu 8.10
If I switch window manager to metacity from compiz, then windows resize and move through an ugly outline, divided into squares. The problem seems to be that when I switch off compiz, visual effects are automatically set to "none", instead of "standart"... And switching them to "standart" then, doesn't help.

Is there a way to fix this? I tried searching options in gconf, but didn't find anything...

-Thanks in advance!
--Artem

---

### Post by sandlidl on 2009-03-11
You can try this: Press "alt F2" and type:

```
metacity --replace
```

Good luck!

---

### Post by Temik on 2009-03-13
I know how to switch to metacity...

The problem is somewhere in metacity configuration itself...

---

### Post by zhocchao on 2009-03-13
look if /apps/metacity/general/reduced_resources is true (gconf). if true change.
z

---

### Post by Temik on 2009-03-15
> **zhocchao said:**
> look if /apps/metacity/general/reduced_resources is true (gconf). if true change.
z

It works =) Everything is great! Thank you :D

---

