---
title: "Keyboard map"
date: 2006-06-11
forum: Desktop Environments
---

### Post by elbryan on 2006-06-11
I really hate this bug..
I'm with KDE and I really don't know why every time I reboot my machine my keyboard map change to English ..

I've setted it to Italian but, after a reboot, it returns to English (although in the keyboard map windows Italian is still the selected map).

This problem there weren't at the fresh install .. 
There's a nice way to reconfigure my keyboard from the beggining?

---

### Post by elbryan on 2006-06-11
please help me .. i hate having to reconfigure it every time ...

---

### Post by tchock on 2006-06-11
Is it set correctly in your /etc/X11/xorg.conf? If it doesn't say:

```
	Option		"XkbLayout"	"it"
```

you could try setting that manually...

---

### Post by elbryan on 2006-06-11
Yes it is .. :( I really don't know what to do ..

---

