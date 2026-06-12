---
title: "Fractional scaling for GDM?"
date: 2020-05-29
forum: Desktop Environments
---

### Post by tozian on 2020-05-29
Is it possible to get fractional scaling in GDM? 100% Scaling is just too small and 200% is just too big. 150% scaling with GNOME seems to work fine with no performance issues and has the most comfortable viewing.

I tried putting the following in /etc/gdm3/greeter.dconf-defaults

```
[org/gnome/desktop/interface]
scaling-factor=uint32 1.5
```

After running ```
dpkg-reconfigure gdm3
``` it tells me there is an invalid character in the number. Is there some other way to comfortable scaling?

(Alternatively, if this is impossible, do any other login managers like LightDM allow for this?)

---

### Post by CatKiller on 2020-05-29
1.5 is not an integer.

According to the Arch wiki you can use ```
text-scaling-factor '1.5'
``` but I've not tried it because I don't use Gnome.

---

### Post by tozian on 2020-05-29
Thank you. I had to remove the quotes in order for it to work however. In order to change the cursor size to match I added:

```
text-scaling-factor=1.5
cursor-size=36
```

---

