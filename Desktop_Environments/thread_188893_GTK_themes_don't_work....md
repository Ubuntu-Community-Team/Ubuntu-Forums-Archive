---
title: "GTK themes don't work..."
date: 2006-06-04
forum: Desktop Environments
---

### Post by xoaqin on 2006-06-04
Why some GTK themes don't work in Dapper Drake?

They work in Ubuntu 5.10 what's wrong?

Can I do anything for them to work?

---

### Post by rbalfour on 2006-06-04
GTK has been upgraded in dapper. some older won't work without tweaking the files. try contacting the creator of the theme.

---

### Post by Sir Alaran on 2006-06-04
[QUOTE=rbalfour]GTK has been upgraded in dapper. some older won't work without tweaking the files. try contacting the creator of the theme.[/QUOTE]

Well, I am "the creator of the theme" in my case. What threw me off is that you need to specifically install "gtk2-engines-pixbuf," an engine that a huge number of themes (including my own) depend on. No need to bother the theme creators.

---

### Post by bvc on 2006-06-05
pixbuf engine is not installed by default? :o 
that's silly since the Gray pixmap theme is installed by default

---

