---
title: "Display striping"
date: 2009-02-22
forum: General Help
---

### Post by terpdan on 2009-02-22
I am having trouble with vertical lines varying in size on my display. At first I thought this was a font rendering problem. I followed all the advice on fonts and rendering settings, sub-pixel smoothing and hinting to no avail. Then i noticed it is not just fonts it shows up in other vertical lines, easiest to notice in maximize/minimize button. It seems to vary in pixel width as i drag across the display....

Good news is i figured how to stop it .... I just can't make it stick

I am running 64 bit intrepid on amd with Nvidia GeForce 6150SE nForce 430, HP w2207 lcd monitor.

If i run the Nvidia X Server Settings package and go into x server display configuration, select either the current setting of auto or the drop down setting of 60 hz and then apply.... success, problem disappears.

only problem is every time i restart the problem is back until i repeat this procedure.

attached is  a screenshot of the server settings.

Any help appreciated

---

### Post by guitar_man on 2009-02-22
It looks fine to me..try adjusting the refresh rate of the monitor
System>Preference>Screen Resolution..try 60hZ on hte refresh rate...hope that helps

---

### Post by terpdan on 2009-02-22
the problem doesn't actually show on a screen capture

system>preferences>Screen resolution only offers me 50hz, 51 hz and 110 hz as option.... no 60hz option

---

### Post by guitar_man on 2009-02-22
have you tried all the option?try each one of them

---

### Post by terpdan on 2009-02-22
The 50hz setting made it go away and survived a restart...

thanks

---

