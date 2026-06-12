---
title: "desktop cube won't work"
date: 2007-09-30
forum: Desktop Effects &amp; Customization
---

### Post by m.ookie on 2007-09-30
My desktop cube doesn't work all of a sudden.

I opened the terminal and typed:

*sudo apt-get install gnome-compiz-manager*

then it read:

[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gnome-compiz-manager[/I]

I'm very new to this and I don't know what to do, so any help would be greatly appreciated.

---

### Post by por100pre1 on 2007-10-01
I'm confused, did it stop working?

This will install everything you may want and more:

```
sudo aptitude install beryl-manager beryl-settings emerald emerald-themes compiz desktop-effects
```

---

### Post by m.ookie on 2007-10-01
thanks for the help.  it's back up again.

---

### Post by Llywelyn on 2007-10-10
Mine stopped working for no apparent reason as well, Feisty since the start. wobbly windows kept working fine. All updates get freedom of my PC as when they come along. Fixed with your tip:

sudo aptitude install beryl-manager beryl-settings emerald emerald-themes compiz desktop-effects

Thanks

---

