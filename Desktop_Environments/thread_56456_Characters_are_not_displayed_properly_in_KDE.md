---
title: "Characters are not displayed properly in KDE"
date: 2005-08-12
forum: Desktop Environments
---

### Post by bkv on 2005-08-12
Hi.

Characters not part of the standard English character set are often displayed as open rectangles. Seems  to happen in KDE applications only. For instance a web page may have this problem in Konqueror but not in Firefox. I'm running KDE 3.4.2 Norwegian.

Does anyone know how to fix this?

-Bjørn

---

### Post by daller on 2005-09-04
What system-locale do you use?

run "dpkg-reconfigure locales" in commandline, and choose the proper locale!

---

### Post by drx on 2005-09-04
I have this experience with Konqueror and fonts that do not contain the needed Unicode charset. Maybe you should try to use a font that is known to have most Unicode characters in it, like Arial. Yes it's not a nice font, but it has all the arrows and weird Umlauts we need. -- Probably in the future KDE should display these characters from another font if they are not found in the present font.

---

### Post by Corlian on 2005-09-04
As I understand, FreeSans also has a good extended character set.  When I first encountered this problem, and I changed system fonts to FreeSans, it also required a reboot to set everything right.

---

