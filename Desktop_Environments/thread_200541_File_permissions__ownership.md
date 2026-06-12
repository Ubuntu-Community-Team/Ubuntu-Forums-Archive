---
title: "File permissions / ownership"
date: 2006-06-20
forum: Desktop Environments
---

### Post by i386DX on 2006-06-20
How can I change the permissions of the owership of more than one file in Gnome (or files within a directory). In Nautilus I only can change one file at the time. So I always have to use the CLI...

Is there an option so I can do this in gnome/nautilus in a graphical way?

---

### Post by givré on 2006-06-20
not yet. I hope it will be possible soon

---

### Post by ayoli on 2006-06-20
not yet sure ? i can change perm of selected files in nautilus, just by select  he files, right-clic then properties, pick the permissions tab. that's works for me.
edit: but i think it's not recursive (it doesn't go into subfolders)

---

### Post by taurus on 2006-06-20
You can do that from a terminal (Applications -> Accessories -> Terminal)
```

chmod -R 744 <filename or directory name>

```

---

### Post by ayoli on 2006-06-20
[QUOTE=taurus]You can do that from a terminal (Applications -> Accessories -> Terminal)
```

chmod -R 744 <filename or directory name>

```[/QUOTE]
yes but i386DX says that he have to always use ocmmand line and don't want to

---

### Post by givré on 2006-06-20
not yet for multiple files :cool:

---

### Post by aysiu on 2006-06-20
Use Konqueror, then.

You can use Konqueror in Gnome.

---

