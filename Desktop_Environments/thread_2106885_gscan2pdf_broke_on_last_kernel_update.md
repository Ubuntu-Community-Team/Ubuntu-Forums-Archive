---
title: "gscan2pdf broke on last kernel update"
date: 2013-01-20
forum: Desktop Environments
---

### Post by makitso on 2013-01-20
Ubuntu 12.04, last update around Jan 19th.  Now gscan2pdf can't find the scan device.  I updated the product to 1.11 but still the same error.  Gimp can find the scanner OK.

Edit:  Ok, tracked the problem down.  I needed to install hplip-gui and then use it to find the wireless printer.  Once this was done then sane was able to find it and as well gscan2pdf.

---

