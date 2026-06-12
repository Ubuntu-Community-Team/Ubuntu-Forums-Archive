---
title: "Compiz Help"
date: 2011-09-21
forum: Desktop Environments
---

### Post by Nath4n on 2011-09-21
Hello guys I need some help with compiz.

OS: 11.04
Running gnome with macbuntu in ubuntu style  with ubuntu tweak and compiz.

Everything runs great but I have lost the magic lamp effect with docky since I did a clean install from 10.10 back to 11.04.  

In fact the entire animations menu in compiz is empty.  I have the plugins and extras installed.  I've tried every solution and I think I need to reinstall compiz.  I'm not sure how to do this or if there is another solution.

Here is the compiz menu:
[IMG]http://i56.tinypic.com/33abhqq.jpg[/IMG]

---

### Post by Nath4n on 2011-09-22
I have uninstalled and reinstalled compiz and still no menu in application.  

I also uins/reinst ubuntu-tweak

I have literally tried every solution on the forum, can anybody help?

Thanks.

---

### Post by Krytarik on 2011-09-22
> **Nath4n said:**
> I have literally tried every solution on the forum, can anybody help?
Really!? Reinstalling those applications is everything that came up? No mention of possibly faulty profile settings, and how to reset them?

If you didn't try this already, reset all Compiz settings to the defaults:
```
gconftool-2 --recursive-unset /apps/compiz
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
```Then relogin.

Hope it helps!

---

