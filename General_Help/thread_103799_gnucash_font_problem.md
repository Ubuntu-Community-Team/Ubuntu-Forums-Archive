---
title: "gnucash font problem"
date: 2005-12-14
forum: General Help
---

### Post by Zaventh on 2005-12-14
Hello,

I recently installed gnucash from the (multiverse?) repository. Upon attempting to start it I get the following:
```

Warning: gnucash_style_set_register...(): Cannot load font: -adobe-helvetica-medium-r-normal--*-120-*-*-*-*-*-*

Fatal Error: gnucash_style_set_register...(): Cannot load fallback font: -adobe-helvetica-medium-r-normal--*-120-*-*-*-*-*-*

Warning: gnucash_style_set_register...(): Cannot load font: -adobe-helvetica-medium-o-normal--*-120-*-*-*-*-*-*

Fatal Error: gnucash_style_set_register...(): Cannot load fallback font: -adobe-helvetica-medium-o-normal--*-120-*-*-*-*-*-*

Fatal Error: gnucash_style_set_register...(): Cannot load fallback font: -adobe-helvetica-medium-r-normal--*-120-*-*-*-*-*-*

Fatal Error: gnucash_style_set_register...(): Cannot load fallback font: -adobe-helvetica-medium-o-normal--*-120-*-*-*-*-*-*

```

I have googled tons of sites and these forums but found no solution on Breezy.

Read this thread too: [http://ubuntuforums.org/showthread.php?t=81813](http://ubuntuforums.org/showthread.php?t=81813)

Same problem, no resolution. Any ideas?

---

### Post by msch on 2006-04-22
Hi-

This is most likely a problem with your xorg.conf.  You need to add all your font paths to make this work.  I added:

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
    FontPath        "/usr/X11R6/lib/X11/fonts/misc/"
    FontPath        "/usr/X11R6/lib/X11/fonts/misc/:unscaled"
    FontPath        "/usr/X11R6/lib/X11/fonts/Type1/"
    FontPath        "/usr/X11R6/lib/X11/fonts/Type1/:unscaled"
    FontPath        "/usr/X11R6/lib/X11/fonts/100dpi/"
    FontPath        "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/X11R6/lib/X11/fonts/75dpi/"
    FontPath        "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
EndSection

To mine and everything is working great now!

---

