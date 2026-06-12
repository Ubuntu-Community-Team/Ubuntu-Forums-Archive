---
title: "Nautilus Elementary status bar theme problem!!!"
date: 2011-05-04
forum: Desktop Environments
---

### Post by samialtas on 2011-05-04
[SIZE=2]Hey fellas. Can anybody help me on that annoying theme problem? Emerald is my default window decorator and I use Ubuntu 11.04 Classic. Thanks...[/SIZE]

[IMG]http://i53.tinypic.com/fvgwfn.jpg[/IMG]

---

### Post by jdorenbush on 2011-05-06
Here's the fix:

Open up the nautilus.rc file in a text editor. The file can be found in: /usr/share/themes/elementary/gtk-2.0/Apps/

Find this code:
```

style "nautilus-statusbar"
{
xthickness	= 0

```

And after it add:
```

ythickness 	= 0

```

---

### Post by samialtas on 2011-05-20
> **jdorenbush said:**
> Here's the fix:

Open up the nautilus.rc file in a text editor. The file can be found in: /usr/share/themes/elementary/gtk-2.0/Apps/

Find this code:
```

style "nautilus-statusbar"
{
xthickness    = 0

```And after it add:
```

ythickness     = 0

```

Thanks buddy, it worked :D

---

