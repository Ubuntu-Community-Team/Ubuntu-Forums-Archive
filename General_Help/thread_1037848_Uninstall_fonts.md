---
title: "Uninstall fonts?"
date: 2009-01-12
forum: General Help
---

### Post by TennSeven on 2009-01-12
I manually installed a font group (MrsEaves, from Mac TTF files) that is showing up in some programs like Scribus, but not in OpenOffice where I need it.  I want to uninstall and re-install the font but I cannot figure out how to do it.

To install I copied the fonts in their own directory to /usr/share/fonts/truetype/ and ran fc-cache.

To uninstall I tried removing the font directory and running fc-cache again ("sudo fc-cache -fv").  However, when I run "fc-list" the fonts still appear in the list.

Any ideas??

---

### Post by cros13 on 2009-01-12
ERK!!!

All I can say is that the best place to install fonts for your
user is in .fonts under your home folder.

You need to clean the font cache again:

sudo fc-cache -f -v

---

