---
title: "Can't load Emerald"
date: 2008-12-13
forum: Desktop Environments
---

### Post by dannytatom on 2008-12-13
I've installed emerald with 'sudo apt-get install emerald'
I go to Applications -> Settings -> Emerald Theme Manager, import a theme, but nothing happens after that.  I've disable "Allow xfce to manage the desktop," also.

Am I missing something? :(

---

### Post by Izek on 2008-12-13
You need to start emerald.

emerald --replace

in terminal.

---

### Post by Epikuma24 on 2008-12-13
don't use emrald just do this:
1. right click on your desktop
2.click change desktop backround
3.go to theme
4.do what ever you want.:p:)

---

### Post by dannytatom on 2008-12-13
> **Izek said:**
> You need to start emerald.

emerald --replace

in terminal.

I've tried this, and I get:

```

(emerald:6690): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8

```

> **Epikuma24 said:**
> don't use emrald just do this:
1. right click on your desktop
2.click change desktop backround
3.go to theme
4.do what ever you want.:p:)

The theme I want says it requires emerald. ;x

---

### Post by dannytatom on 2008-12-14
So, I've been looking into this for a while and it seems that I need Compiz for Emerald to work.  I installed compiz, but it too won't start.  I found Compiz-Check, ran it, and this is the output:

```

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   Xfce
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 

```

What confuses me, is that I had compiz running with gnome, but now that I'm using xfce I get all these errors.  I'm lost. ;x

---

