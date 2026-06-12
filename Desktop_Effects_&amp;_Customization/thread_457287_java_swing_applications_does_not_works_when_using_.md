---
title: "java swing applications does not works when using beryl"
date: 2007-05-28
forum: Desktop Effects &amp; Customization
---

### Post by legolas_w on 2007-05-28
Hi
Thank you for reading my post
my java based swing application does not works correctly when i use beryl in ubuntu 7.04.
what should i do?

thanks

---

### Post by gsmayya on 2007-05-30
putting

*export AWT_TOOLKIT=MToolkit*

before calling the actual program might help. Can wrap the call through a small script..
It helped me to render sqldeveloper (a java application) properly under beryl.

---

### Post by usien on 2007-05-30
if you are developing this application yourself, you should consider using SWT for better support on linux.

---

