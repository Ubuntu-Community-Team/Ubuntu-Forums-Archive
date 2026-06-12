---
title: "bsetroot problem"
date: 2007-05-28
forum: Desktop Effects &amp; Customization
---

### Post by satellite360 on 2007-05-28
bsetroot doesn't work for me when I input a hexadecimal value, so
```
bsetroot -solid black
```
works, but
```
bsetroot -solid #000000
```
doesn't.  This is annoying as most downloadable styles come hex values filled in.  The gradient feature also doesn't work.

Any idea how I can get round this?  Is there another program I can use in place of bsetroot?

I'm using the Blackbox wm.

Thanks

---

### Post by yabbadabbadont on 2007-05-28
Does it work if you use this instead?
```
bsetroot -solid '#000000'
```

If not, install eterm, then use Esetroot.  It is generally considered to be the most full featured app for setting the root window background.

---

### Post by satellite360 on 2007-05-30
Thanks - adding the quote marks did the trick.

Still can't get the gradient -from and -to to work with hex values but am not too bothered about that.

---

