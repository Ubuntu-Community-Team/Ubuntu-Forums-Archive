---
title: "Firefox has really small menu and links text..."
date: 2005-12-09
forum: Desktop Environments
---

### Post by Goddess_of_Linux on 2005-12-09
Firefox isn't my favorite browser (Konquerer and Safari are), but I want to make Firefox usable as well and when I told adept to go and get firefox and install it, I had a problem with the menu bar and linux text appearing really small (5pt font or less like), but the web pages appear as regular 12 point and higher font. I don't understand what is wrong there.

---

### Post by GeneralZod on 2005-12-09
Have you tried gtk2-engines-gtk-qt?

[http://ubuntuforums.org/showthread.php?t=22232&highlight=gtk2-engines-gtk-qt](http://ubuntuforums.org/showthread.php?t=22232&highlight=gtk2-engines-gtk-qt)

---

### Post by Goddess_of_Linux on 2005-12-11
I'm using Breezy Kubuntu and the stock apt sources.list... when I type in the following sudo apt-get install gtk2-engines-gtk-qt This is what appears: > Reading package lists... Done Building dependency tree... Done gtk2-engines-gtk-qt is already the newest version. 0 upgraded, 0 newly installed, 0 to remove and 79 not upgraded. So I install very gtk2-engines thing I could find and that didn't work neither. 

I am trying removing all the installed gtk2-engines that it installed and seeing if that will work

---

### Post by dto on 2005-12-11
I don't think it will. 

Since gtk2-engines is already installed, have you tried going to System Settings > Appearance and clicking on GTK styles and fonts? From there you can select themes and fonts for GTK-based applications.

---

### Post by Goddess_of_Linux on 2005-12-11
After uninstalling everything that gtk2-engines-gtk* installed and reinstalling the gtk2-engines-gtk-qt worked. But what I hadn't did was tell the control center that I wanted the gtk fonts to be one particular size and not rely on what I have KDE set as. Thanks for your help.

EDIT= Both of you, thanks...

---

### Post by OneWingedAngel on 2005-12-11
Try setting the Display Resolution to 'Use System Setting' in Firefox.
(I had this problem too, and variants of it with Fx & Opera on my Gentoo system)

---

