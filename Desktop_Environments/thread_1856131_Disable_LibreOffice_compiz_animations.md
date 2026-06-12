---
title: "Disable LibreOffice compiz animations"
date: 2011-10-07
forum: Desktop Environments
---

### Post by AndyBoy_LV on 2011-10-07
Hello!


Does anybody know how to disabled compiz animations for LibreOffice? Because i am using "Skewer" animations for opening/closing windows, and it turns out that LibreOffice menus and tooltips are using it too... Which is very annoying. 


Can anyone help me with it?

---

### Post by Copper Bezel on 2011-10-07
LibreOffice's menus register as "Utility" rather than "Menu" windows. Remove the word "Utility" from the rule for Skewer.

Edit: Also, you just solved a problem with OpenOffice on my desktop that has been bothering me for *three years* by asking that question, so thanks. = D

---

### Post by Krytarik on 2011-10-07
> **Copper Bezel said:**
> LibreOffice's menus register as "Utility" rather than "Menu" windows. Remove the word "Utility" from the rule for Skewer.
I'd rather exclude LibreOffice explicitly, like this:
```
(type=Utility & !class=LibreOffice)
```Regards.

---

### Post by Copper Bezel on 2011-10-07
Good call. Thanks for the correction.

---

### Post by AndyBoy_LV on 2011-10-08
Thank you guys! That solved my problem :)

---

