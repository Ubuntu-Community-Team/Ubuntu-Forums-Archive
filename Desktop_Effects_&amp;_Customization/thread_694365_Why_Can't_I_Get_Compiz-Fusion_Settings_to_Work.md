---
title: "Why Can't I Get Compiz-Fusion Settings to Work????"
date: 2008-02-12
forum: Desktop Effects &amp; Customization
---

### Post by avkhatri on 2008-02-12
I installed Compiz-Fusion and I got the settings manager and none of my hotkeys work, the fire wont work the water wont work. I set my hotkeys I press them and NOTHING happens. Before I installed compiz I installed GLdesktop, it is what gave me the origional cube. Could Gldekstop be conflicting with the Compiz-Fusion? This is just really frustrating I don't get why none of this will work.

---

### Post by mrmiserable on 2008-02-12
in terminal what is ouput of

```
compiz
```

---

### Post by shafin on 2008-02-12
What do you have as backend? Gconf or Flat File?

Examine in CompizConfigSettings>Preferences,if you have GConf as Backend,change it to flat file and try again.

---

