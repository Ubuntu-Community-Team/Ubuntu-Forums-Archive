---
title: "firefox fails to start"
date: 2012-07-13
forum: Desktop Environments
---

### Post by D0natell0 on 2012-07-13
Hi,
Firefox won't start, either when I click the desktop icon or from the command line.
Error like this - 
"Firefox could not start. Profile may be missing"

I tried it in safe mode from the command line but got the same error.

I tried uninstalling from the Ubuntu Software Centre and re-installing - still get the same error! :confused:

Ubuntu 12.04LTS.
Intel Core2Duo.
RAM 2GB.

Thanks!

---

### Post by roijac on 2012-07-13
Try to remove firefox, delete ~/.mozilla/firefox and install it again.

---

### Post by D0natell0 on 2012-07-13
fixed! :p

I couldn't delete the ~/.mozilla/firefox because I'd already done that in earlier attempt to fix it.

Instead, I uninstalled, deleted ~/.mozilla and re-installed. That's working now.
Many thanks!
:guitar:

---

