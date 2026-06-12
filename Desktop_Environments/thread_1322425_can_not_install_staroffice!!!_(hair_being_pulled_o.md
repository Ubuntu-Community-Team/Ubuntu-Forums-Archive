---
title: "can not install staroffice!!! (hair being pulled out)"
date: 2009-11-10
forum: Desktop Environments
---

### Post by Gunnder on 2009-11-10
I am trying to install staroffice from the command line following this guide:
 [https://help.ubuntu.com/community/StarOffice](https://help.ubuntu.com/community/StarOffice)
(I've been looking all across the web for the last 3 days and I keep running into the same error.  I'm just missing a step or something)

I keep getting the error:
sh: Can't open so-91-bin-linux-en-us.sh

I have the file downloaded into Downloads folder, in command line this is what I'm doing,  I can't figure out what I'm missing.

I'm new to ubuntu so any help will be appreciated.

root@Mini-Gig:/home/brian/Downloads# sh so-91-bin-linux-en-us.sh
sh: Can't open so-91-bin-linux-en-us.sh

Open Office is completly removed.  I have used staroffice for years and am just more comfortable with it (not that big of a difference between the two, just personal preference)

Thanks

---

### Post by gazreen on 2009-11-11
try this:
# chmod a+x open so-91-bin-linux-en-us.sh
and then 
# sh open so-91-bin-linux-en-us.sh

---

### Post by Gunnder on 2009-11-11
Thanks gazreen,

I got it going now!

I'll spend the time while its loading gluing my hair back in.  Big learning curve using the command line compared to windows, but well worth it.

Thanks

---

