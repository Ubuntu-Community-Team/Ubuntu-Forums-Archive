---
title: "How-To: GTK-style or KDE-style for OpenOffice2"
date: 2005-12-13
forum: Desktop Environments
---

### Post by linkunderscore on 2005-12-13
I use FVWM instead of Gnome, but I do like the gtk settings that come with gnome because they make the applications look pretty :) After I had installed OpenOffice2 I noticed that it looked really ugly and the gtk settings weren't being used.

If you want OpenOffice2 to not look like crap with its nasty default "theme", you can do the following:

```
sudo gedit /usr/lib/openoffice2/program/soffice
```

Add the following line to the top of the script:

for gtk
```
export OOO_FORCE_DESKTOP=gnome
```

for kde
```
export OOO_FORCE_DESKTOP=kde
```

Save the file and voila! The next time you start any openoffice2 applications the appropriate settings should be applied. 

*FYI--If OpenOffice2 is ever updated, you may (probably will) have to re-edit the soffice script.*

Hope this helps!

---

### Post by Kimm on 2005-12-23
Thanks, thats just what I needed (XFCE4) ^^

---

### Post by linkunderscore on 2005-12-29
Im glad I could help. It took me almost a month to figure out this solution.

---

