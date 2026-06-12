---
title: "Issue with installing font"
date: 2009-02-02
forum: General Help
---

### Post by BinaryApe on 2009-02-02
I'm trying to install a font I found on gnome-look.org. The font is Vibrocentric : [http://www.dafont.com/vibrocentric.font](http://www.dafont.com/vibrocentric.font)

I have seen several other screen shots with people using it.

I have downloaded it and put it in my usr/share/fonts/TrueType directory and it appears in the list for me to select as my default font under System-> Preferences -> Appearance -> Fonts I can select it.

But when I pick the font it comes up as nothing but a bunch of white square boxes. I can view the font if I double click on it with the font viewer. Anyone have any idea what could be wrong?

When I run the command fc-cache -fv to cache the fonts it doesn't recognise the files as a font.

I am using the latest Nvidia drivers 180.27 on a Geforce 7950 GX2 if that makes a difference.

---

### Post by BinaryApe on 2009-02-02
I fixed the issue by finding an older version of the font. NOw it works. 

For some reason the new font compilation (done in like 2002-2004) won't work. But the font made in 1998 will. Oh well, I guess it is just fixed

---

