---
title: "No &quot;System Fonts&quot; are working in Dapper Drake after running the new ATI drive install"
date: 2006-10-15
forum: Desktop Environments
---

### Post by ALWAYSRU on 2006-10-15
I downloaded the latest ATI drivers and ran through the install (ati-driver-installer-8.29.6.run). After the install finished (used all the default options during the install), my screen looked like the attached screenshot.

I've tried reinstalling the x-window-system-core package, libcairo2 package (was told that has something to do with font rendering), as well as the gnome and gdm packages. None of those things worked. 

I feel like the ATI install must have removed my main system fonts but I cannot figure out how to reinstall/change them to something that does exist on the system.

I've also tried doing the alt+f2 to run qtconfig to change the system font, but when I hit alt-f2, I get a screen like the second screenshot.

Has anyone else seen this? Any idea how to fix it?

---

### Post by ALWAYSRU on 2006-10-18
Bump... please. I need help here.

---

### Post by dagnabit dang doohickey on 2006-10-18
You may want to try [this]("http://ubuntuforums.org/showpost.php?p=1616953&postcount=10").

---

### Post by mcduck on 2006-10-18
Could you paste your xorg.conf here?

(for example, you can run 'cat /etc/X11/xorg.conf > ~/Desktop/xorg.txt' and attach the created text file from your desktop here..)

edit: also, the right tool for configuring fonts in gnome is 'gnome-font-properties', go to System/Preferences/Font. qtconfig is for KDE apps.

---

### Post by ALWAYSRU on 2006-10-18
My xorg.conf is attached here now.

Thanks!

---

### Post by ALWAYSRU on 2006-10-18
> **mcduck said:**
> Could you paste your xorg.conf here?

(for example, you can run 'cat /etc/X11/xorg.conf > ~/Desktop/xorg.txt' and attach the created text file from your desktop here..)

edit: also, the right tool for configuring fonts in gnome is 'gnome-font-properties', go to System/Preferences/Font. qtconfig is for KDE apps.


Thanks for the 'gnome-font-properties' hint. When I ran it, I got all sorts of errors about "pango", decided to google it and it turns out that it is a package that changes how fonts are rendered. Went to [http://ftp.gnome.org/pub/GNOME/sources/pango/](http://ftp.gnome.org/pub/GNOME/sources/pango/) and downloaded the source for the 1.15.0 version then ran (as root):
```
tar -xvzf pango-1.15.0.tar.gz
cd pango-1.15.0
./configure
make
make install

```
Rebooted and my system is back to healthy! (see the happy working system screenshot!!!)

Maybe the ATI drivers installed an incompatible version of pango? Anyone have any insights? 

Anyways, problems fixed. Thanks for the ideas!

---

### Post by mcduck on 2006-10-20
> **ALWAYSRU said:**
> 
Maybe the ATI drivers installed an incompatible version of pango? Anyone have any insights? 

Anyways, problems fixed. Thanks for the ideas!
Coul be. Or then the installer just messed something up. I'm using the drivers from Ubuntu's repositories myself.

But it's great that you got your fonts working again :)

---

