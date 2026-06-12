---
title: "Transparent inactive/passive windows"
date: 2010-10-26
forum: Desktop Environments
---

### Post by allinthegame on 2010-10-26
Hi

I've recently started using Ubuntu and I'm hoping this isn't a stupid question:

I want to make the windows that don't have focus transparent i.e. the active window opacity is 100 while all the passive windows have a lower opacity.

I've had a good look around compiz config (including the opacity and opacify settings) and google and can't seem find what I want. I'm using Ubuntu 10.10 and the latest version of compiz config.

In the compiz wiki there is a plug-in called _[COLOR=Blue][trailfocus]("http://wiki.compiz.org/Plugins/Trailfocus")[/COLOR]_ and I think this does what I want but I don't have it installed in compiz config atm, is it possible to add this plugin?

Thanks

---

### Post by stinkeye on 2010-10-27
The trailfocus plugin is in the **compiz-fusion-plugins-extra** package.

To install via the terminal enter:
```
sudo apt-get install compiz-fusion-plugins-extra
```

In ccsm you will find it in the effects category.

---

### Post by allinthegame on 2010-10-27
Thanks for that, works like a charm!

---

