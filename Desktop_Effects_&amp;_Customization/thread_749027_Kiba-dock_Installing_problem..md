---
title: "Kiba-dock Installing problem."
date: 2008-04-08
forum: Desktop Effects &amp; Customization
---

### Post by m1n054 on 2008-04-08
I'm getting these errors after typing sudo make install in kiba-dock-plugins:

```
na-tray-manager.c:41:24: error: na-marshal.h: No such file or directory
na-tray-manager.c: In function 'na_tray_manager_class_init':
na-tray-manager.c:154: error: '_na_marshal_VOID__OBJECT_STRING_LONG_LONG' undeclared (first use in this function)
na-tray-manager.c:154: error: (Each undeclared identifier is reported only once
na-tray-manager.c:154: error: for each function it appears in.)
na-tray-manager.c:166: error: '_na_marshal_VOID__OBJECT_LONG' undeclared (first use in this function)
make[3]: *** [na-tray-manager.lo] Error 1
make[3]: Leaving directory `/home/m1n05/kiba-dock/kiba-plugins/plugins/tray'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/m1n05/kiba-dock/kiba-plugins/plugins'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/m1n05/kiba-dock/kiba-plugins/plugins'
make: *** [install-recursive] Error 1
```

I couldn't find any file named na-marshal.h so that could be the problem.
Help please? Thanks.

---

### Post by Ignacio Monge on 2008-04-08
Same problem here. This happens since I've upgraded to GNOME 2.22.1.

---

### Post by m1n054 on 2008-04-08
Could it be some header file from the gnome environment? Or is it not related?

---

