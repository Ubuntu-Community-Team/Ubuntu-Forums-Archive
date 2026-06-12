---
title: "Desktop Effects: Gnome &amp; KDE"
date: 2007-05-25
forum: Desktop Effects &amp; Customization
---

### Post by usudave on 2007-05-25
I started off with Ubuntu (Edgy Eft), with which the desktop effects work wonderfully.

I then installed the KDE environment, which also installed without a problem.

However, the desktop effects don't work in KDE when I switch to it, and I see no option to turn them on. Would anyone happen to know how I can get the desktop effects to work in KDE? I suppose that what I've done would be slightly different from Kubuntu as far as what comes default and out of the box. 

Thanks!

---

### Post by loathsome on 2007-05-25
Try to run ```
compiz --replace
```

Though, there's no support for KWin in Compiz yet.

---

### Post by Mazza558 on 2007-05-25
Try installing beryl, which will automatically switch the Window Manager to Beryl.

---

### Post by Ateo on 2007-05-25
Yea. Beryl works best with KDE. You'll also need Emerald or other window decorator.

---

### Post by loathsome on 2007-05-25
I figured that Compiz is actually 100% compatible with KDE when you install the 'compiz-kde' package;)

---

### Post by SneakyBooBoo on 2008-06-03
right, i followed the instructions to get compiz working in KDE but i dont think i want it anymore cos it increases my boot up time (old laptop). so how do i disable it now?

i ran 

# compiz --disable

and that seemed to work but then my title bars went missing. when i tried to change the normal KDE window decoration nothing happened. so i rebooted and compiz and emerald were back again. what now?

---

