---
title: "KDE + Composite breaks menu fonts in libre office"
date: 2012-02-18
forum: Desktop Environments
---

### Post by gltripp on 2012-02-18
Hello all!

I've a strange problem with libre office, running under KDE 4.7.4:

nearly all menu entries in libreoffice are somehow broken. there is just a line or nothing, where the menu entry should be. (see screenshot)
as soon as I disable composite in kde, the menue entries appears again and everything looks normal.

This behaviour affects only libreoffice. i've no problems with any other application while compositing is enabled.

Does anybody know this problem and can give me a clue how to fix this?


thanks at all

---

### Post by AlmaTlust on 2012-02-28
It actually is a combination of kde compositing enabled and font smoothing enabled in libreoffice... I don't know how to fix this, really, only a workaround:
either disable font smoothing completly in libreoffice or put it to at least 13pt (depending on your configuration).

---

### Post by caco3 on 2012-04-04
Thank you for your tip!
Disabling the font aliasing in LibreOffcie solved the issue. The fonts now dont look nice, but at least we can read it. Hopefully this will get fixed sometimes.

(Note: In LibreOffice I also enabled the checkbox "Use systemfonts" which makes it look a bit nicer in my case).

---

### Post by AlmaTlust on 2012-04-04
There is a better solution as well. In systemsettings, go to "application display - fonts" (or similar, my language  is set to German) and play around with font smoothing settings until it works. The settings that work for me are "smoothing - enabled" and Force dpi for fonts to 96dpi (resolution of my lcd screen).

---

