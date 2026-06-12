---
title: "compiz fusion without emerald"
date: 2007-06-28
forum: Desktop Effects &amp; Customization
---

### Post by kpkeerthi on 2007-06-28
How do I start compiz without emerald? I'm using 
```

compiz --replace -c emerald

```

which works fine... but I just want to get rid of emerald. I tried ```
compiz --replace
``` but I ended up with no window border :(

---

### Post by tuxcantfly on 2007-06-28
do you have compiz-gnome installed? Does the command

```
gtk-window-decorator --replace
```

do anything? If not, install compiz-gnome... Try this for startup:

```
compiz --replace -c gtk-window-decorator
```

---

