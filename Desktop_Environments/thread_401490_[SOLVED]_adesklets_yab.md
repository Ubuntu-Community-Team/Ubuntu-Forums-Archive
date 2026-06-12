---
title: "[SOLVED] adesklets yab"
date: 2007-04-04
forum: Desktop Environments
---

### Post by borobudur on 2007-04-04
Hi,
I installed **adesklets** and added with the GUI (adesklets -i) the **yab** desktop bar.


Now, how do I start that thing? If I put
```
adesklets --nautilus
```nothing is happening.

Thanks for your help
borobudur

PS. using Gnome

---

### Post by johnc4510 on 2007-04-04
I've never used adesklets, but with gdesklets you just type gdesklets in a terminal and then enable things through the panel icon.  So I'm guessing you should try typing adesklets in a terminal to initiate the app.

Hope this helps

---

### Post by yabbadabbadont on 2007-04-04
You have to manually run yab once in order to register it.  Open a terminal and cd into the yab directory.  (probably ~/.desklets/yab-XXXXX)  Then run, "./yab" and take the option to register it when asked.  (It may be called something other than just yab, as it may have a version number on the end)  After it has been registered, it should then show up when you run "adesklets --nautilus".

---

### Post by borobudur on 2007-04-04
That's what I did but no reaction of adesklet.

I'm using gdesklets but there is no yab.

---

### Post by yabbadabbadont on 2007-04-04
If you are using either compiz or beryl, then you will probably have problems.  This has been reported in the past as a known issue with adesklets.

---

### Post by borobudur on 2007-04-04
That's it! Thank yabbadabbadont_!_

---

