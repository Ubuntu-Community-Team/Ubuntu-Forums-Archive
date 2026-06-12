---
title: "probly easy, but dealing with the app menu"
date: 2009-04-06
forum: General Help
---

### Post by stackbaxter on 2009-04-06
every now and again, i'll install a prog. using add/rem and it will appear in the app menu but refuses to launch, and through my own newbness am unable to find it using the file browser, my current one is K3b.  any help would be lovely.

cheers

-S

---

### Post by cariboo on 2009-04-06
If you installed k3b completely, it should show up in Applications-->Sound & Video, I have installed k3b many times and never had a problem with it. To locate where the executable was installed open a Terminal and type:

```
locate k3b
```

Generally application executables get installed in /usr/bin.

Jim

---

### Post by stackbaxter on 2009-04-06
I just reinstalled, and the same thing, it won't launch.

so I :

stackbaxter@stackbaxter-desktop:~$ locate k3b
/usr/share/app-install/desktop/kde_k3b.desktop
/usr/share/app-install/icons/k3b.xpm
/usr/share/icons/oxygen/128x128/apps/k3b.png
/usr/share/icons/oxygen/16x16/apps/k3b.png
/usr/share/icons/oxygen/22x22/apps/k3b.png
/usr/share/icons/oxygen/32x32/apps/k3b.png
/usr/share/icons/oxygen/48x48/apps/k3b.png
/usr/share/icons/oxygen/64x64/apps/k3b.png

it looks to me like somethings missing...?

thx

-S

---

