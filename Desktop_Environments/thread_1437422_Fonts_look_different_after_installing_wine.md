---
title: "Fonts look different after installing wine"
date: 2010-03-23
forum: Desktop Environments
---

### Post by Harry Muscle on 2010-03-23
I installed Wine on my machine just a few minutes ago and as part of the installation the following packages are also installed: ttf-liberation, 
ttf-mscorefonts-installer, ttf-symbol-replacement, ttf-tahoma-replacement.  These add extra fonts to the system which I'm assuming are required by windows programs running inside Wine.  The problem is though that Firefox also seems to be using these fonts because the fonts now look different inside Firefox.  Not a huge difference, but you can tell they are different and they just don't look "right" to the eye.  They are no longer as pleasing as they were when Firefox was using the default Ubuntu fonts.

Is there a way to keep these fonts for use by Wine, but not allow any other program on Ubuntu to use them?

Thanks,
Harry

---

### Post by byStanderone on 2010-03-23
...this thread would be of help, i guess :
[http://ubuntuforums.org/archive/index.php/t-974111.html](http://ubuntuforums.org/archive/index.php/t-974111.html)

---

### Post by mexp on 2010-04-15
I'm having this same problem, the thread above didn't offer any solutions.

It seems that in this thread someone had a similar problem: [http://ubuntuforums.org/showthread.php?t=412782](http://ubuntuforums.org/showthread.php?t=412782)

But how to fix this?

---

### Post by Djzn.BR on 2011-05-27
Seems like when you do run the wine configuration, something gets screwed. Firefox rendering and UI fonts go ugly, and LibreOffice also gets crazy fonts. 

I found out that if you remove the file **.fonts.conf** and directory **.fontconfig** and also the **.wine** directory, then log out and log back in, the fonts will be fixed.

So this is something wineconfig is doing...

---

