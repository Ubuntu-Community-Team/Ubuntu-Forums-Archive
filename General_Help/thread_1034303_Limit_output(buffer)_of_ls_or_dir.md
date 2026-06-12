---
title: "Limit output(buffer) of ls or dir"
date: 2009-01-08
forum: General Help
---

### Post by James- on 2009-01-08
I want to limit the output on the screen of ls or dir
kinda like

xxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxx
(Press enter to continue)

I know windows can do it..but how do we do it under linux/unix?

---

### Post by bbabu84 on 2009-01-08
Pipe the output to "more":
ls | more
You can also use "less" which is a little bit more than "more"!
ls | less

---

