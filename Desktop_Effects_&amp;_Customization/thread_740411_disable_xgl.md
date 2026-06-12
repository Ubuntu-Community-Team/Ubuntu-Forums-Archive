---
title: "disable xgl"
date: 2008-03-30
forum: Desktop Effects &amp; Customization
---

### Post by supersonicdarky on 2008-03-30
How can I non-destructively (easy to undo) disable xgl and replace it with X instead? Since i'm not using compiz anymore, I have no need for xgl and it is quite a resource hog (15% + ram and keeps growing as time goes on, X only takes 2-3% on my laptop).  If possible, have it run X in openbox, but Xgl in gnome.

---

### Post by santiagoward2000 on 2008-03-30
> **supersonicdarky said:**
> How can I non-destructively (easy to undo) disable xgl and replace it with X instead? Since i'm not using compiz anymore, I have no need for xgl and it is quite a resource hog (15% + ram and keeps growing as time goes on, X only takes 2-3% on my laptop).  If possible, have it run X in openbox, but Xgl in gnome.

Hi!
In Gusty, you just have to create an empty file called **disable** in **~/.config/xserver-xgl**
I'm not sure if it's the same for Hardy.
Cheers!

---

