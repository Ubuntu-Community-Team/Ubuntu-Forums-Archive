---
title: "gxine setup wizard driver question"
date: 2005-08-06
forum: Desktop Environments
---

### Post by FNM on 2005-08-06
After using the gxine setup wizard, under the "Check for MIT Xv extension" area, I get a popup that says "you can improve performance by installing an X11 driver that supports the Xv protocol extension". I then get a popup that says "libx11.so: cannot open shared object file: No such file or directory. I can play DVDs just fine, but I was wondering what this message means exactly, and how I can fix it.

---

### Post by FNM on 2005-08-06
Anyone?

---

### Post by Xterminator on 2005-08-07
I don't use XV extension ,install the **libx11-6-dev** package
my pref is **xshm**

```
sudo apt-get install libx11-6-dev
```

and make a simlink ;-)

```
 sudo ln -s /usr/X11R6/lib/libX11.so.6.2 /usr/X11R6/lib/libx11.so
```

run

```
sudo ldconfig
```

and rerun gxine setup wizard :-)

---

### Post by FNM on 2005-08-07
[QUOTE=Xterminator]I don't use XV extension ,install the **libx11-6-dev** package
my pref is **xshm**

```
sudo apt-get install libx11-6-dev
```

and make a simlink ;-)

```
 sudo ln -s /usr/X11R6/lib/libX11.so.6.2 /usr/X11R6/lib/libx11.so
```

run

```
sudo ldconfig
```

and rerun gxine setup wizard :-)[/QUOTE]

Thanks, worked like a charm.

---

