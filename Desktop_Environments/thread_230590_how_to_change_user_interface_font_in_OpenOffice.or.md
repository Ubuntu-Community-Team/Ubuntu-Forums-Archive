---
title: "how to change user interface font in OpenOffice.org 2?"
date: 2006-08-06
forum: Desktop Environments
---

### Post by evaldas on 2006-08-06
Hi,

i'm using Xubuntu 6.06 with XFCE DE.
I have installed msttcorefonts and using Tahoma 8 font as a default user interface font in XFCE. Everything works perfectly, except in openoffice. Openoffice uses some other font (not Tahoma) for its user interface. If I check/uncheck "use system font for user interface" - nothing changes.
[here]("http://madpenguin.org/cms/index.php/?m=show&id=141") I found tip to use 'font replacement', but there's no Andale Sans UI font in the dropdown box.

---

### Post by evaldas on 2006-08-07
*bump*

---

### Post by Sanne on 2006-08-13
This also bugged me since I installed Kubuntu 6.06 lately, because using the Andale font from the tip doesn't work (just type it directly into the drop down field). I just found the fix for my system, maybe it helps you also:

In OpenOffice go to Tools/Options/Fonts, choose "DejaVu Sans" in the left drop down field, choose the font you want to replace it with in the right field, click the green ok icon to the right to get this replacement pair into the table beneath.

In the table line, check "Always" and "Screen", click ok (maybe "Screen" isn't necessary, try both).

If this still doesn't work, try other fonts as "DejaVu Sans", which apparently is the font OOo uses for the interface on my system.

EDIT: clarifications

Hope this helps, greetings, Sanne

---

