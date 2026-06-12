---
title: "FireFox Menu Bar Fonts Adjustable?"
date: 2005-06-30
forum: Desktop Environments
---

### Post by zote on 2005-06-30
Using Kubuntu installed over Ubuntu, changing the fonts though the control gui does not seem to affect the fonts in FireFox as it does with Konqueror.  Is there a way to basically enlarge or change the fonts in the menu bar and menu lists for FireFox and I suppose also Thunderbird?

---

### Post by dresnu on 2005-06-30
You can take a look here for changing the firefox interface [http://www.mozilla.org/support/firefox/edit](http://www.mozilla.org/support/firefox/edit) (don't know about thunderbird but it must something similar). Firefox is compiled with gtk libraries, that's why the changes you apply don't take effect, so as second solution you could install the GTK-QT Engine (you find it in the repos) in order to change the style and the fonts of every gtk application running under kde.

---

### Post by chandra on 2005-07-01
You need to edit your userChrome.css file.  Take a look at:

Customizing Mozilla
[http://www.mozilla.org/unix/customizing.html](http://www.mozilla.org/unix/customizing.html)

---

