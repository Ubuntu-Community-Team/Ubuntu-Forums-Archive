---
title: "Convert all filenames to UTF-8"
date: 2005-07-04
forum: Desktop Environments
---

### Post by rykel on 2005-07-04
Hi,

1.   How do I convert all my filenames (ie. my whole system) to use UTF-8?

The reason is that I have files and folders that are written in Japanese or Chinese, but which appear as gabbage on my system. (eg. "**??*&%$$$!?????**.pdf)

Another related problem is when I tried the latest BitTornado downloaded from Ubuntu  backports, with its new GTK2 interface (nice!), it CANNOT download any files with a Chinese/Japanese encoding. I did not have such errors with the older version, which is based on GTK1, I believe.

2.   How do I know which encoding is my system using currently?

Thanks for your help!!

Best Regards,

Rykel
Gizmo.Skype.eBay.MSN.Yahoo: **rykel98**

---

### Post by Knome_fan on 2005-07-04
1. I found convmv to be pretty good for converting filenames to utf-8.
(I think it's in universe, but if it isn't here's the url: [http://j3e.de/linux/convmv/](http://j3e.de/linux/convmv/))

2. Open up a terminal and run sudo locale

---

### Post by rykel on 2005-07-04
Hi,

Thanks for the suggestion on convmv. I will run it later, but meanwhile, this is what sudo locale reported to me... seems like my system is already UTF-8, except the last line, "LC_ALL"...

Regards,

Rykel
Gizmo.Skype.eBay.MSN.Yahoo: rykel98

LANG=en_SG.UTF-8
LC_CTYPE="en_SG.UTF-8"
LC_NUMERIC="en_SG.UTF-8"
LC_TIME="en_SG.UTF-8"
LC_COLLATE="en_SG.UTF-8"
LC_MONETARY="en_SG.UTF-8"
LC_MESSAGES="en_SG.UTF-8"
LC_PAPER="en_SG.UTF-8"
LC_NAME="en_SG.UTF-8"
LC_ADDRESS="en_SG.UTF-8"
LC_TELEPHONE="en_SG.UTF-8"
LC_MEASUREMENT="en_SG.UTF-8"
LC_IDENTIFICATION="en_SG.UTF-8"
LC_ALL=
_____________________________________________________________________________

UPDATE:

OK, I am lost... how do I convert my system fully to UTF-8 using convmv?

Or just a single folder for that matter?

Please advise, thanks!!

---

### Post by adamkane on 2006-03-05
convmv Nautilus script
[http://www.ubuntuforums.org/showthread.php?t=139154](http://www.ubuntuforums.org/showthread.php?t=139154)

---

