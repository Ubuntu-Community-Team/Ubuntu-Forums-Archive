---
title: "Can't install extensions in Gnome 3"
date: 2013-01-24
forum: Desktop Environments
---

### Post by Ranko Kohime on 2013-01-24
In my most recent OS swap, (which is becoming far too much of a habit), I chose the masochists route and installed from the minimal CD, while preserving the multi-generation home folder I've been dutifully filling full of junk for years.  ):P

I then proceeded to install Gnome-Shell, and lo and behold, I can't load extensions from extensions.gnome.org.  The error it gives on the page is:
```
You do not appear to have an up to date version of GNOME3. You won't be able to install extensions from here. See the about page for more information.
```

So, am I missing a package, or perhaps a config file needs trashing?

---

### Post by Ranko Kohime on 2013-01-24
Well, solved my own problem, and now I feel silly for not noticing sooner.  :oops:

For those reading this with the same problem, make sure that the Gnome Shell Integration plugin is active in your browser, check either [about:plugins]("about:plugins") for Firefox or [chrome://plugins]("chrome://plugins") for Chromium.

---

