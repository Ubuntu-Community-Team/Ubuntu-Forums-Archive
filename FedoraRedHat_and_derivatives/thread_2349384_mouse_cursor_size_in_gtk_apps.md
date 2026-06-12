---
title: "mouse cursor size in gtk apps"
date: 2017-01-14
forum: Fedora/RedHat and derivatives
---

### Post by mattdawolf on 2017-01-14
This is probably not only related to CentOS 7. 

I have 3 4k displays and I sit at least six feet away. Resoltion is set to 2160p. KDE's large cursor theme lets me set it to 64 pixels. When in firefox and thunderbird, the cursor has its own theme and is scaled down to the smallest setting. 

Any idea how I can force a setting of 64 pixels for gtk apps? I tried GTK-chtheme but that did not work.

---

### Post by Dennis N on 2017-01-14
To get consistent theme in Korora 25 (a respin of Fedora 25), I created a hidden text file .Xdefaults in my home folder with contents:

```
Xcursor.theme: FlatbedCursors.White.Large
```

Without it, I had a problem similar to yours in that after log in, the cursor theme would often revert back to the default Adwaita in some places. The cursor theme I use above has only one size, so I don't have the size problem. If you need to specify a size for a resizable cursor, try adding another line, like:

```
Xcursor.size: 56
```

to the same file.

No guarantee this will work in CentOS, but worth a try.

---

