---
title: "installing Wine 1.1.3 in Ubuntu 9.04"
date: 2009-04-26
forum: General Help
---

### Post by whlspacedude on 2009-04-26
Hi,
Im new here, but not too new to linux.(first post)
i have been trying to install wine 1.1.3 in ubuntu 9.04 i cannot get it to install.
using sudo apt-get install wine i can install wine 1.1.2 but i want to use 1.1.3
when i use the wine-1.1.3.tar.bz2 from winehq i get these errors

freetype.c:166: error: ‘FT_MulFix’ undeclared here (not in a function)
freetype.c:166: warning: type defaults to ‘int’ in declaration of ‘pFT_MulFix’
freetype.c: In function ‘WineEngGetOutlineTextMetrics’:
freetype.c:5142: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5143: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5145: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5153: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5153: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5157: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5161: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5241: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5242: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5243: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5244: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5245: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5246: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5247: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5248: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5249: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5254: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5255: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5256: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5257: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5258: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5259: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5260: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5261: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5262: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5263: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5268: error: called object ‘pFT_MulFix’ is not a function
freetype.c:5269: error: called object ‘pFT_MulFix’ is not a function
make[2]: *** [freetype.o] Error 1
make[2]: Leaving directory `/home/will/Desktop/wine-1.1.3/dlls/gdi32'
make[1]: *** [gdi32] Error 2
make[1]: Leaving directory `/home/will/Desktop/wine-1.1.3/dlls'
make: *** [dlls] Error 2

Compilation failed, aborting install.




can any one be of help?
thanks

---

### Post by __j__ on 2009-05-23
I got the same result compiling from the Jaunty repo sources. Building from Wine 1.1.22 works fine.

The issue appeared to be that the offending function in FreeType, FT_MulFix, was inlined for performance as of FreeType 2.3.8. (Jaunty packages 2.3.9.)

---

### Post by Penguinish on 2009-05-23
hey i installed wine a few days ago, but i did this.

I went to system>adminstartion>synaptic package manager

did a search for wine, right clicked it and marked for installation and hit apply. It installed on my system and works fine

---

### Post by __j__ on 2009-05-23
> **Penguinish said:**
> hey i installed wine a few days ago, but i did this.

I went to system>adminstartion>synaptic package manager

did a search for wine, right clicked it and marked for installation and hit apply. It installed on my system and works fine

That's the easiest way to go if you're just trying to install Wine, yes. The errors above were from building Wine from sources.

---

