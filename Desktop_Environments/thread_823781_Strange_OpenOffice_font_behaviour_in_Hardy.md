---
title: "Strange OpenOffice font behaviour in Hardy"
date: 2008-06-09
forum: Desktop Environments
---

### Post by ashwinjm on 2008-06-09
Just upgraded to Hardy, and everything seems to have gone well... Except for OpenOffice which has started rendering documents which were perfectly OK under Gutsy in strange ways.

For instance, text in the bold AlArabiya font randomly italicizes letters, which seems to vary by font size - 10.5 is ok, 11 is messy, 12 is slightly less so, and 13 looks ok too.

The Garuda and Mallige fonts, on the other hand, look completely different from Gutsy, much uglier than they were.

Anyone know what might be going on? Thanks!

---

### Post by ajgreeny on 2008-06-09
May not be anything to do with your problem, but have you set font rendering up for your monitor?  Right click on an empty desktop area and then go to change background, but then the font tab, where you can set rendering to what you want, or what is best for your monitor.

---

### Post by ashwinjm on 2008-06-09
Thanks - but I tried different font rendering settings already. Seems like something got broken with font packages over the upgrade, but I'm not sure yet if its a problem with my system, or an OpenOffice bug...

---

### Post by pytheas22 on 2008-06-09
I'm not sure if it's related, but it's worth mentioning that with OpenOffice 2.3 in Gutsy, I started having problems one day where certain characters, in any font, were displayed incorrectly.  For instance, if I wanted to make é, I got È instead; ä came out as something like %a.  It only happened in OpenOffice; if I copied and pasted the text into gedit, it displayed correctly.  Also it only seemed to happen with characters that are not standard in U.S. English, the language setting of my system.  Upgrading to OO 2.4 solved the problem.

Unfortunately I never figured out what the cause was; there's a bug report somewhere for it, but the resolution given was to upgrade to OO 2.4.  In your case, purging and reinstalling OO might help (2.5 is not available yet, although there is a beta for 3.0 I think).  You could also try installing the Debian build of OO from the [openoffice.org]("http://download.openoffice.org/other.html#en-US") website instead of the version in the Ubuntu repositories.

Sorry I can't offer a real solution, but I thought my issue was worth mentioning in case it helps to point you in the right direction.

---

### Post by ashwinjm on 2008-06-09
Thanks, but this seems different - regular alphabetical characters are also affected, with random italicization and ugly font rendering. I will try nuking my OpenOffice and reinstalling it to see if that helps.

---

