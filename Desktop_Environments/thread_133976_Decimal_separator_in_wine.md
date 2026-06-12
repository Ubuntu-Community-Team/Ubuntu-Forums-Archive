---
title: "Decimal separator in wine"
date: 2006-02-21
forum: Desktop Environments
---

### Post by F_W on 2006-02-21
Does anyone know how to change the decimal separator for Window$ programs running in wine from comma "," to decimal point "." (some  progs need this). In Window$ this can be done via the regional setting menu, but in wine...?

Thanks
Franz

---

### Post by rolfington on 2008-01-21
You can do this via regedit. Start regedit by typing:

$ regedit

In the regedit tree you go to:

My Computer -> HKEY_CURRENT_USER -> Control Panel -> International

Here you can change sDecimal, sMonDecimalSep, sMonThousandSep and sThousand to a preferred character. You will also be able to change other locale settings such as currency, time/date format, etc.

Cheers,
Rolfington

---

