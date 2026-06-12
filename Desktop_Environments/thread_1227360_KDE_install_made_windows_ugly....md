---
title: "KDE install made windows ugly..."
date: 2009-07-30
forum: Desktop Environments
---

### Post by PhoHammer on 2009-07-30
I installed KDE after XFCE and everything is going great, except the windows are now
ugly and don't change with the theme...

Did I miss something while installing all KDE's goodies?

here's a screenshot to illustrate:

---

### Post by Zorael on 2009-07-30
Do you have the **kde-style-qtcurve** and **gtk2-engines-qtcurve** packages installed?

GTK apps look like that unless you install those and tell KDE to handle them with care, in System Settings -> Appearance -> GTK Styles and Fonts. GTK Styles, Use another style: **Qtcurve**. Then log out and back in.

---

### Post by PhoHammer on 2009-07-30
> **Zorael said:**
> Do you have the **kde-style-qtcurve** and **gtk2-engines-qtcurve** packages installed?

GTK apps look like that unless you install those and tell KDE to handle them with care, in System Settings -> Appearance -> GTK Styles and Fonts. GTK Styles, Use another style: **Qtcurve**. Then log out and back in.

Thanks! Worked like a charm. Although, judging by your sig, I figured it might:)

---

