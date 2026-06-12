---
title: "error restarting kde plasma desktop"
date: 2017-06-16
forum: Desktop Environments
---

### Post by roberto32 on 2017-06-16
Plasma panel crashes from time to time - so I try to restart plasma 
```
 
kbuildsycoca5 && kquitapp5 plasmashell && kstart5 plasmashell  
```  
but this is what I get: 
```

kbuildsycoca5 running...
kf5.kservice.sycoca: Parse error in  "/home/roberto/.config/menus/applications-merged/xdg-desktop-menu-dummy.menu" , line  1 , col  1 :  "unexpected end of file"
The desktop entry file "/usr/share/applications/evolution-data-server-uoa.desktop" has Type= "Application" but no Exec line
kf5.kservice.sycoca: Invalid Service :  "/usr/share/applications/evolution-data-server-uoa.desktop"
"Application plasmashell could not be found using service org.kde.plasmashell and path /MainApplication."

```
when I try ```
 [COLOR=#393939][FONT=Consolas]killall plasmashell [/FONT][/COLOR]
``` or ```
 [COLOR=#393939][FONT=Consolas]killall plasma-desktop[/FONT][/COLOR] 
```  no process found...

FYI - I installed Xubuntu, then I installed kde-plasma-desktop

---

### Post by SeijiSensei on 2017-06-16
The easiest solution is to log out and log back in.  You can also force a new desktop by killing X, but  logging out is cleaner.

---

