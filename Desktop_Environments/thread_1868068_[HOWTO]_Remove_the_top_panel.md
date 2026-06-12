---
title: "[HOWTO] Remove the top panel"
date: 2011-10-23
forum: Desktop Environments
---

### Post by tonysathre on 2011-10-23
If you are like me and hate that top panel (File | Edit | View | etc) you can remove it with the following two commands:

```
apt-get remove appmenu-gtk
apt-get remove appmenu-gtk3
```

Took me a day to figure this out so I figured I'd share it in case anyone else was wondering.

Tony

---

### Post by cbowman57 on 2011-10-23
Can't you also alt+r-click on it in the panel &  remove it?

Been awhile since I've used fallback mode but I seem to remember that worked.

---

### Post by tonysathre on 2011-10-23
> **cbowman57 said:**
> Can't you also alt+r-click on it in the panel &  remove it?

Been awhile since I've used fallback mode but I seem to remember that worked.

No. I tried right-clicking on it but it did nothing. No context menu at all. Same with Alt+RClick.

---

### Post by cbowman57 on 2011-10-23
Interesting, I just installed those two packages & logged into classic mode & didn't see any changes to my top panel.  I built this from minimal though so Unity was never installed, wonder if that alters the behavior?

---

