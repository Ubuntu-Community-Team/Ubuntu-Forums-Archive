---
title: "username logon text HUGE"
date: 2007-05-04
forum: Desktop Environments
---

### Post by miatawnt2b on 2007-05-04
Standard Ubuntu upgrade to Fiesty Fawn, now username logon text appears as huge letters, as well as the password bubbles.

What happened, and how can I change the font size for logon text?

Thanks,
-J

---

### Post by ComplexNumber on 2007-05-04
imagine that you using the Human gdm, right? if so go to /usr/share/gdm/themes, then open up the file called Human.xml using the following command on the commandline:
**gksudo gedit /usr/share/gdm/themes/Human.xml**

do a search for "font" and see if you can see any overly large fonts being used.



i can't think what would make them go huge. is there any other application where the fonts are affected in this way?

---

### Post by miatawnt2b on 2007-05-04
Yep, I found the user/pass logon font size and decreased it to 10pt.  PERFECT!
Thanks!
-J

---

