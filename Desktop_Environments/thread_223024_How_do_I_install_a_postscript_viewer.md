---
title: "How do I install a postscript viewer?"
date: 2006-07-25
forum: Desktop Environments
---

### Post by kjhgfkh on 2006-07-25
I tried: sudo apt-get install gsview

and it did not work.  Could somebody please clue me in?

Thank you.

---

### Post by llamakc on 2006-07-25
ken@dothan:~$ apt-cache search postscript | grep view
evince-gtk - Document (postscript, pdf) viewer
kghostview - PostScript viewer for KDE
advi - an active DVI previewer and presenter
bmv - PostScript viewer for SVGAlib
epstool - edit preview images and fix bounding boxes in EPS files
gfontview - font viewer for Type 1 and TrueType fonts
gnome-gv - GNOME PostScript viewer
gv - PostScript and PDF viewer for X
mozplugger - Plugin allowing external viewers to be launched inside Mozilla
sylpheed-claws-ghostscript-viewer - PostScript/PDF viewer plugin for the Sylpheed Claws mail client
wv - Convert and preview Microsoft Word documents
xnecview - NEC structure and gain pattern viewer
xpdf-reader - Portable Document Format (PDF) suite -- viewer for X11
acroread - Adobe Acrobat Reader: Portable Document Format file viewer
evince - Document (postscript, pdf) viewer


Install one of the viewers like evince. Works great. Is it not already installed?

---

### Post by Dr Gonzo on 2006-07-25
```
sudo apt-get install gv
```
It's not pretty, but it's fast and works every time. :)

---

