---
title: "Firefox is acting weird"
date: 2009-05-08
forum: General Help
---

### Post by _sluimers_ on 2009-05-08
Hi, my firefox is no longer functioning normally.

* I'm no longer asked for the master password
* Youtube or any other embedded video file no longer works
* Any animated pic is now shown static and half transparent.
* Some png files are completely transparent (showing the 'it's invisible gray tiles') on webpages unless I open them.

What happened?

---

### Post by blazemore on 2009-05-08
It sounds like a problem with your Firefox profile.
There are a few ways of fixing this, by the easiest and most common is to simply remove Firefox completely, and then reinstall it.

You can do this by opening a terminal windows (Applications > Accesories > Terminal) and typing the following command:
```
sudo aptitude purge firefox -y && sudo aptitude install firefox -y
```

---

### Post by _sluimers_ on 2009-05-11
That didn't work :eek:

Any other suggestions?

---

