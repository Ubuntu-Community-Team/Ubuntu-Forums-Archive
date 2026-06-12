---
title: "the battery applet in Cairo-dock opengl"
date: 2010-01-06
forum: Desktop Environments
---

### Post by jackubun on 2010-01-06
I meet a problem when I use cairo dock.
I try to launch Battery applet, but what I got is just a blank place. and the space could show the battery information by words.

However, if I use cairodock -c, which is not the opengl version. I could see the battery gauge icon. Are there any body having this problem? How can I fix this problem in cairo dock opengl?

Thanks!

---

### Post by fabounet on 2010-01-06
this is fixed in the current beta version (2.1.3-beta)

there is a dedicated PPA on Launchpad for it.

also, if you have an Intel card, you may want to try with indirect rendering (cairo-dock -oi)

---

### Post by jackubun on 2010-01-06
Thanks a lot!
I fix it using -oi command!

---

