---
title: "How to remove &quot;cd/dvd creator&quot; from places menú?"
date: 2007-08-15
forum: Desktop Environments
---

### Post by Marcelo Ramone on 2007-08-15
[FONT=Arial][SIZE=3][COLOR=black]How to remove "cd/dvd creator" from places menu?

Thanks in advance.-[/COLOR][/SIZE]
[/FONT]

---

### Post by praet on 2007-08-16
That menu item is created with this file:
```
/usr/share/applications/nautilus-cd-burner.desktop
```

You could also remove the nautilus integrated cd burner software:
```
$ sudo apt-get remove nautilus-cd-burner
```

---

### Post by rsambuca on 2007-08-16
> **praet said:**
> That menu item is created with this file:
```
/usr/share/applications/nautilus-cd-burner.desktop
```

You could also remove the nautilus integrated cd burner software:
```
$ sudo apt-get remove nautilus-cd-burner
```

That is really not a good idea if you want to upgrade ubuntu to the next version.  The above command will remove the ubuntu-desktop metapackage, so while it is OK to do so, remember that you will have to re-install it later prior to upgrading ubuntu.

---

### Post by praet on 2007-08-16
Yes that is correct, and additionally, to reinstall you will need your ubuntu cd handy.
If it were me i would just remove the menu item.

---

### Post by Marcelo Ramone on 2007-08-16
[SIZE="3"][B]Thank you Both.

I will remove the menu entry only.

I'm using Brasero for burn CDs/DVDs and I don't like this entry in places menu.[/B][/SIZE]

---

