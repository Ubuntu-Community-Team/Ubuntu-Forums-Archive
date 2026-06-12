---
title: "Hardware acclerated mouse pointer."
date: 2006-09-12
forum: Desktop Environments
---

### Post by joshier on 2006-09-12
Hello.. how to I change my mouse from software acclerated to hardware acclerated?.. because for some odd reason, my graphics driver for my openchrome graphics display makes my mouse pointer disappear on certain software GUI's, for example, when using windows applications under Wine, and the new beta firefox (the navi buttons to be specific makes my pointer hide)

I know it just hides and doesn't stop moving because if I focus enough using a windows application on wine, I am able to roughly guess where my mouse pointer is and click the nessessary button.. though this isn't acceptable if I want to use it a lot.

Thanks

---

### Post by theboomboomcars on 2006-09-13
To get your mouse cursor back add this line:
        Option          "SWCursor"
to your openchrome device section.  I had the same problem and this fixed it.

---

