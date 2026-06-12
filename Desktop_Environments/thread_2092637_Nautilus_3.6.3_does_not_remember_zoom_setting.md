---
title: "Nautilus 3.6.3 does not remember zoom setting"
date: 2012-12-08
forum: Desktop Environments
---

### Post by glaubersm on 2012-12-08
I use nautilus 3.6.3 installed by Gnome 3 Team PPA, it does not remember zoom settings, step to reproduce the problem...
open nautilus (use icon view)
increase the zoom using ctrl+mouse wheel
restart nautilus
Rssult: zoom level is 100% again

Is there any workaround to solve this problem?

I use Ubuntu 12.10 Gnome Remix x32

---

### Post by glaubersm on 2012-12-10
Nothing?

---

### Post by greenhillbilly on 2013-04-01
I had this problem then I realised - dconf!

I think dconf is already installed. You can use it to set many different preferences.

Open dconf then in the left hand expandable menu go to - +org+gnome+nautilus then "preferences" and "list-view" - you can set the default view and zoom levels here.

---

### Post by greenhillbilly on 2013-04-01
Sorry - and "icon-view"

---

### Post by jbicha on 2013-04-10
If you open Preferences, you can set the default zoom level.

---

