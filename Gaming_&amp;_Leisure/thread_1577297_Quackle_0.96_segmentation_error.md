---
title: "Quackle 0.96 segmentation error"
date: 2010-09-18
forum: Gaming &amp; Leisure
---

### Post by Ronin_R on 2010-09-18
hey!

I searched the forums for scrabble in ubuntu,found some topics,discovered Quackle
Was pretty excited to get going on it.
Installed .deb package
but it is showing "segmentation error" when I try to run it.

I downloaded the source code and tried to build it according to instructions in readme
hardluck
same result :(

I am using Ubuntu 10.04 Lucid Lynx
Intel Core2Quad
2 GB RAM
Nvidia GeForce 9500 GT Graphics card

hope to play Quackle soon :)

---

### Post by oldrocker99 on 2010-09-18
Segmentation errors are almost always a video driver problem. You have installed nVidia's Linux drivers, correct?

:guitar:

---

### Post by Ronin_R on 2010-09-19
@oldrocker99

thanks for showing interest.

Yes I have installed Nvidia accelerated graphics driver (version 173 )

any workaround to get it working ? :-)

---

### Post by mwgourmet on 2011-01-04
Same problems here

Running 11.04 on ASUS U-35

Tried the source-code, but I get errors from the fixstring.h file

Any thoughts?

---

### Post by P-Nuts on 2011-03-09
It compiles fine from source if you add a few include directives.

```
--- quackle-0.96/datamanager.h	2008-07-23 07:54:37.000000000 +0100
+++ quackle-0.96-new/datamanager.h	2011-03-09 18:24:05.346605000 +0000
@@ -22,6 +22,7 @@
 #define QUACKLE_DATAMANAGER_H
 
 #include <string>
+#include <cstdlib>
 
 #include "playerlist.h"
 
--- quackle-0.96/fixedstring.h	2008-07-23 07:54:37.000000000 +0100
+++ quackle-0.96-new/fixedstring.h	2011-03-09 18:23:08.314605001 +0000
@@ -22,6 +22,8 @@
 #define QUACKLE_FIXEDSTRING_H
 
 #include <cassert>
+#include <string>
+#include <cstring>
 
 #define FIXED_STRING_MAXIMUM_LENGTH 40

```

---

