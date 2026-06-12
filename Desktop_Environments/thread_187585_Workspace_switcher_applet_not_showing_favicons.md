---
title: "Workspace switcher applet not showing favicons"
date: 2006-06-03
forum: Desktop Environments
---

### Post by mpiktas on 2006-06-03
In Ubuntu Breezy, the workspace switcher applet would show the icon of application if it is maximized in the workspace. I think it usually showed the icon from application's .desktop file.   For epiphany it was even more cool, the favicon of the website was shown. In Ubuntu Dapper this feature is gone. The applet shows maximized windows  as dull rectangles, and I am sad:-|   So my question would be if this is a regression due to upgrade, or is there something wrong in my configuration?

---

### Post by scb147 on 2006-06-03
Same here... I thought I had them when I first installed, but I just noticed earlier today that they were gone.  I just searched and found that if you change the size of the gnome panel the workspace switch is on, they will come back when enlarged.  I had to increase mine to 26 pixels.

---

### Post by mpiktas on 2006-06-07
[QUOTE=scb147]Same here... I thought I had them when I first installed, but I just noticed earlier today that they were gone.  I just searched and found that if you change the size of the gnome panel the workspace switch is on, they will come back when enlarged.  I had to increase mine to 26 pixels.[/QUOTE]

Thanks, that solved the problem. My panel was 24 pixels and favicons showed in normal X server, but not in XGL. After increasing to 26 I can see favicons in XGL too. Sadly epiphany favicon does not change according to current site's favicon. But having XGL I can live with that :)

---

