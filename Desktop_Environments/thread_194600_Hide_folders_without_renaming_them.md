---
title: "Hide folders without renaming them?"
date: 2006-06-11
forum: Desktop Environments
---

### Post by REBELinBLUE on 2006-06-11
Does anyone know if you can hide folders without renaming them to .name? I know you can use a file named /.hidden up that only appears to work for folders in /

I have Zend Studio installed, which stores its configuration in ~/ZDE and vmplayer which recreates ~/vmware everytime it is launched.

Any ideas how I would hide them?

---

### Post by mannheim on 2006-06-11
[QUOTE=REBELinBLUE]Does anyone know if you can hide folders without renaming them to .name? I know you can use a file named /.hidden up that only appears to work for folders in /

I have Zend Studio installed, which stores its configuration in ~/ZDE and vmplayer which recreates ~/vmware everytime it is launched.

Any ideas how I would hide them?[/QUOTE]

The ".hidden" thing works in any directory, and causes nautilus to hide the members of that directory whose names appear in the file ".hidden". So create a file ~/.hidden and add lines to it like "ZDE" etc. The file manager will then hide ~/ZDE.

---

### Post by REBELinBLUE on 2006-06-11
d'oh! Of course, it is so obvious. I tried that at first but I think I must have been using the full path to the folder or using ".hide" rather than ".hidden"

Thanks

---

