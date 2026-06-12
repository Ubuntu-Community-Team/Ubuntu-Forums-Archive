---
title: "Skype Theme Problem"
date: 2009-12-09
forum: Desktop Environments
---

### Post by naz37 on 2009-12-09
Skype-2.1.0.47 from the medibuntu repository has themeing issues with Ubuntu Netbook Remix 9.10. The font and background colour on the drop down menu are the same and are unreadable unless you mouse over them.

[[IMG]http://imgur.com/Vmo8i.png[/IMG]](http://imgur.com/Vmo8i.png)

It would appear the skypes Qt theme isn't correctly detecting and using the default gtk theme. Anyone got a way of fixing this?

Thanks

---

### Post by naz37 on 2009-12-09
This seem to be a known issue and has a [bug]("https://bugs.launchpad.net/medibuntu/+bug/476398") Medibuntu bugzilla.

Disabling skypes cleanlooks theme seems the only way so far to fix it.

Launch skype with;
```
skype --disable-cleanlooks
```

---

### Post by Raphae1 on 2010-05-26
The new skype version 2.1.0.81 actually has an option in the General-tab, which lets you choose your "Style". Choosing "desktop-style" works as expected.

---

