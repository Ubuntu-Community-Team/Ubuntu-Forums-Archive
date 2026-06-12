---
title: "gtk theme doesn't work on every apps"
date: 2009-12-27
forum: Desktop Environments
---

### Post by mnml on 2009-12-27
Hi,
I would like to know how I can solve that, my gtk theme isn't working on every apps, here is an example.

[IMG]http://img15.imageshack.us/img15/2194/screenshotff.png[/IMG]

---

### Post by jonest1 on 2009-12-27
I came across this a couple days ago.  When running synaptic you are actually using the settings of the root user account.  The root user is not aware of your individual settings.

You can do something similar to the following to ensure root has your themes.

```
sudo ln -s ~/.themes /root
sudo ln -s ~/.icons /root
```

I'm not in front of my system, but I think you can do this for .fonts as well.  I'll update later, when I have a chance to look, but it worked for me.

---

### Post by jonest1 on 2009-12-28
I just double-checked my pc and I linked .themes, .icons, and .fonts.  I tested it out and it works.

---

### Post by mnml on 2009-12-28
thanks it works

---

### Post by t1nm@n on 2010-01-11
copy the the theme file to /usr/share/themes:)

---

