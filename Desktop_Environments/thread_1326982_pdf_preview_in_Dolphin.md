---
title: "pdf preview in Dolphin"
date: 2009-11-14
forum: Desktop Environments
---

### Post by akahige on 2009-11-14
I'm running Gnome with the KDE libs on Karmic.

Was just reading about Dolphin and thought I'd try it out. Seems pretty cool, but I can get it to do pdf preview. In googling around, I found a mention in a SUSE support forum that said the pdf preview was dependent on Okular, so I tried installing that -- but to no avail.

Don't know if that info was wrong, or if there's something I have to do to get Dolphin to recognize that Okular is there for it to take advantage of (or what). There's no "pdf" option in the Dolphin preview selector.

Anybody got any thoughts?

---

### Post by Wadywady on 2010-03-29
Hi!

I had the same problem -- and found a solution at [https://bugs.kde.org/show_bug.cgi?id=167052#c7](https://bugs.kde.org/show_bug.cgi?id=167052#c7)
> . . . package kdegraphics-strigi-plugins was missing. Installing this package brought the pdf preview dolphin at last !
Entering the following in Terminal will install the package:
```
sudo apt-get install kdegraphics-strigi-plugins
```

Cheers!

---

### Post by akahige on 2010-04-02
Awesome!

Thanks for posting.

---

### Post by Tsu jan on 2010-11-29
In Debian, I had the same problem. kdegraphics-strigi-plugins wasn't enough; ghostscript should also be installed for PDF preview to work in Dolphin and Konqueror.

---

