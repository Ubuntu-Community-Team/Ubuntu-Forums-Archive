---
title: "KDE installation question?"
date: 2009-06-06
forum: Desktop Environments
---

### Post by Coldhearth on 2009-06-06
Hi there,

I'm currently reinstalling my ubuntu machine and I was wondering if it is possible to install KDE and deinstall GNOME or visa versa?
I would like to make a good looking desktop so I think KDE will beter suit my needs for themes and stuff... :)

---

### Post by bryonak on 2009-06-06
If you want KDE right from the start, why not download Kubuntu and install that?

Otherwise you can also do this post-install via Synaptic or the terminal. Since latter is faster (to write down, that is ;)), I'll give you those instructions:
```
sudo aptitude install kde
```
Then log out and click on Sessions in the login window. Choose KDE, log in as usual. If you still feel like really removing Gnome, open a terminal:
```
sudo aptitude remove libgnome2-0
```

Simple, isn't it?
I'm not sure how much cleanup is needed for every last bit of Gnome to get removed... you might want to use "aptitude purge" instead of "aptitude remove".
Also it probably won't be as "clean" as installing Kubuntu anyway... for example you'll be still using gdm as login manager. You can change that, but it won't make a big difference

---

