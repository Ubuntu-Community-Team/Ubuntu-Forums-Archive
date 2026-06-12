---
title: "Scribus Doesn't look native"
date: 2011-04-27
forum: Desktop Environments
---

### Post by Timtro on 2011-04-27
Hi All,

Thank you all in advance.

Today I did a fresh install of 11.04 (beta), but I have the same problem on my 10.10 box too. However, I know it's not right, since my laptop and upstairs box (both running 10.10) look fine.

The problem is that Scribus looks like a Windows 95 application. I assume that the problem may be with the Qt support.

I installed the Qt setting manager and set the theme to GTK+, but it had no effect.


Many thanks,



Tim.

---

### Post by Copper Bezel on 2011-04-27
Weird. Scribus is based on Qt3, and Qt3 can actually be configured separately from Qt4, which is what your usual Qt apps are using. They can be configured with the packages qt4-qtconfig and qt3-qtconfig, respectively. However, no changes I make in the latter have any effect on Scribus.

I think it's just ugly.

Edit: Poking around, I am finding some screenshots of it looking a little more presentable under KDE, so that last bit is inaccurate.

---

### Post by Timtro on 2011-04-28
I purged scribus and installed ScribusNG and now it's fine. But I I think if I had just reinstalled regular scribus, it would have been fine too. But that's just a guess.

---

### Post by Copper Bezel on 2011-04-28
No, that worked for me, too. Scribus-stable really *is* just ugly.

---

