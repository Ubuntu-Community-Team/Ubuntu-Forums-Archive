---
title: "change theme in icewm"
date: 2009-03-12
forum: Desktop Environments
---

### Post by mobinskariya on 2009-03-12
How can i change the default theme in a livecd with icewm using CLI???
I have already integrated icewm in the livecd, but i want to change its default theme.
thanks in advance.

---

### Post by BenB1 on 2010-01-31
If you already know which theme you want try:

$ echo themename tee ~/.icewm/theme

That ought to put the theme's name as the zero on the list in the theme file.
There is probably another way to do it. But this is off the top of my noggin
after midnight. HTH

---

