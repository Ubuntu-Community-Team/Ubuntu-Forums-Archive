---
title: "Gnumeric Chart Problem"
date: 2007-07-14
forum: Education &amp; Science
---

### Post by brharri1 on 2007-07-14
When I highlight my data and click "insert chart" (or the chart icon), the window comes up but in the area "plot type" there are no choices. I can't create any type of chart! Does anyone know how to fix this?

---

### Post by akniss on 2007-07-14
> **brharri1 said:**
> When I highlight my data and click "insert chart" (or the chart icon), the window comes up but in the area "plot type" there are no choices. I can't create any type of chart! Does anyone know how to fix this?

Hmmm... that certainly doesn't sound right.  Have you tried reinstalling?
```
sudo aptitude reinstall gnumeric
```

---

### Post by my_key on 2009-01-14
> **brharri1 said:**
> When I highlight my data and click "insert chart" (or the chart icon), the window comes up but in the area "plot type" there are no choices. I can't create any type of chart! Does anyone know how to fix this?

I have the exact same problem. Reinstalling doesn't help.

---

### Post by jbrefort on 2009-01-15
Which version are you using?
The problems comes from uninstalled or deactivated goffice plugins. Using the command "Tools/Plug-ins...", you will have to check the charting plugins you need, and things should work. gnumeric 1.6 and earlier presented this issue when compiled without gnome support. This should not be anymore the case with 1.8+.

---

### Post by jbrefort on 2009-01-16
Tested with intrepid and confirmed. Non native file formats are not supported either, all plugins are deactivated.

---

