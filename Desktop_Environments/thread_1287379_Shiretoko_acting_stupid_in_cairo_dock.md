---
title: "Shiretoko acting stupid in cairo dock"
date: 2009-10-10
forum: Desktop Environments
---

### Post by bigdee973 on 2009-10-10
this really eeks my crack.  upgraded to 3.5, in cairo dock i have a launcher in the bottom..usually when you launch a program and minize the program it'll go directly into the launcher you clicked.  However. since upgrading the default firefox. when you click the firefox launcher it creates another icon/launcher.  How can i get it where i will not create other launchers when i open firefox...the icon i see is simply the blue planet without the fox wrapped around it and how can i rename everything to just be firefox instead of shiretoko

---

### Post by fabounet on 2009-10-10
edit your launcher, and fill its class
you can find it with "xprop | grep CLASS" then clicking on the shiretoko window

---

### Post by bigdee973 on 2009-10-10
> **fabounet said:**
> edit your launcher, and fill its class
you can find it with "xgrep | grep CLASS" then clicking on the shiretoko window

whoa im sorry explain it to me in a dumb dumb way i never heard of this before.  how do i find the class of this launcher and all that? i never heard of this. try to explain what i should do step by step.

---

### Post by fabounet on 2009-10-12
ok sorry
open firefox
then in a terminal, type ```
xprop | grep CLASS
```
then click on the firefox window
in the terminal, you'll have 2 strings, one is the class of firefox.
Now, edit your firefox launcher in the dock (right-click -> modify), go to the "extra parameters", and copy the class insode the corresponding field, and validate.

---

### Post by wesley.jordan on 2009-12-18
> **fabounet said:**
> edit your launcher, and fill its class
you can find it with "xprop | grep CLASS" then clicking on the shiretoko window

Thank You!!  This has been driving me nuts ever since I switched to Cairo-Dock.  I was forever clicking the launcher and creating another instance.

---

