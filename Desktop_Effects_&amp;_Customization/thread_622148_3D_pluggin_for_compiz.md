---
title: "3D pluggin for compiz"
date: 2007-11-24
forum: Desktop Effects &amp; Customization
---

### Post by subs on 2007-11-24
I have tried installing the 3D plugin for compiz on ubuntu gutsy....

whenever i give the command 

> make

i get an error saying...

> [: 1: ==: unexpected operator
-e compiling : 3d.c -> build/lib3d.lo3d.c:54: error: expected specifier-qualifier-list before 'PaintTransformedScreenProc'
3d.c: In function 'tdPaintWindow':
3d.c:260: error: 'tdScreen' has no member named 'paintWindow'
3d.c:261: warning: passing argument 3 of 'w->screen->paintWindow' from incompatible pointer type
3d.c:261: warning: passing argument 4 of 'w->screen->paintWindow' makes pointer from integer without a cast
3d.c:261: error: too few arguments to function 'w->screen->paintWindow'
3d.c:262: error: 'tdScreen' has no member named 'paintWindow'
3d.c:262: warning: assignment from incompatible pointer type
3d.c:270: error: 'tdScreen' has no member named 'paintWindow'
3d.c:271: warning: passing argument 3 of 'w->screen->paintWindow' from incompatible pointer type
3d.c:271: warning: passing argument 4 of 'w->screen->paintWindow' makes pointer from integer without a cast
3d.c:271: error: too few arguments to function 'w->screen->paintWindow'
3d.c:272: error: 'tdScreen' has no member named 'paintWindow'
3d.c:272: warning: assignment from incompatible pointer type
3d.c: In function 'tdPaintTransformedScreen':
3d.c:292: error: 'CompScreen' has no member named 'paintTransformedScreen'
3d.c:292: error: 'tdScreen' has no member named 'paintTransformedScreen'
3d.c:293: error: 'CompScreen' has no member named 'paintTransformedScreen'
3d.c:294: error: 'tdScreen' has no member named 'paintTransformedScreen'
3d.c:294: error: 'CompScreen' has no member named 'paintTransformedScreen'
3d.c:294: error: 'CompScreen' has no member named 'paintTransformedScreen'
3d.c: In function 'tdPaintScreen':
3d.c:307: error: 'tdScreen' has no member named 'paintScreen'
3d.c:308: warning: passing argument 2 of 's->paintScreen' from incompatible pointer type
3d.c:308: warning: passing argument 3 of 's->paintScreen' makes integer from pointer without a cast
3d.c:308: error: too many arguments to function 's->paintScreen'
3d.c:308: error: void value not ignored as it ought to be
3d.c:309: error: 'tdScreen' has no member named 'paintScreen'
3d.c:309: warning: assignment from incompatible pointer type
3d.c: In function 'tdDonePaintScreen':
3d.c:356: error: 'tdScreen' has no member named 'donePaintScreen'
3d.c:358: error: 'tdScreen' has no member named 'donePaintScreen'
3d.c: In function 'tdInitScreen':
3d.c:558: error: 'tdScreen' has no member named 'paintTransformedScreen'
3d.c:558: error: 'CompScreen' has no member named 'paintTransformedScreen'
3d.c:558: error: 'CompScreen' has no member named 'paintTransformedScreen'
3d.c:559: error: 'tdScreen' has no member named 'paintWindow'
3d.c:559: warning: assignment from incompatible pointer type
3d.c:560: error: 'tdScreen' has no member named 'paintScreen'
3d.c:560: warning: assignment from incompatible pointer type
3d.c:561: error: 'tdScreen' has no member named 'donePaintScreen'
3d.c: In function 'tdFiniScreen':
3d.c:577: error: 'CompScreen' has no member named 'paintTransformedScreen'
3d.c:577: error: 'tdScreen' has no member named 'paintTransformedScreen'
3d.c:578: error: 'tdScreen' has no member named 'paintWindow'
3d.c:579: error: 'tdScreen' has no member named 'paintScreen'
3d.c:580: error: 'tdScreen' has no member named 'donePaintScreen'
3d.c: At top level:
3d.c:715: warning: initialization from incompatible pointer type
3d.c:716: warning: initialization from incompatible pointer type
3d.c:717: warning: initialization from incompatible pointer type
3d.c:718: warning: initialization from incompatible pointer type
3d.c:719: warning: initialization from incompatible pointer type
3d.c:720: warning: initialization from incompatible pointer type
3d.c:721: warning: initialization from incompatible pointer type
3d.c:722: warning: initialization from incompatible pointer type
3d.c:723: warning: initialization from incompatible pointer type
3d.c:724: warning: initialization from incompatible pointer type
3d.c:725: warning: initialization from incompatible pointer type
3d.c:729: warning: excess elements in struct initializer
3d.c:729: warning: (near initialization for 'opacityVTable')
3d.c:730: warning: excess elements in struct initializer
3d.c:730: warning: (near initialization for 'opacityVTable')
3d.c:731: warning: excess elements in struct initializer
3d.c:731: warning: (near initialization for 'opacityVTable')
3d.c:732: warning: excess elements in struct initializer
3d.c:732: warning: (near initialization for 'opacityVTable')
3d.c:734: warning: excess elements in struct initializer
3d.c:734: warning: (near initialization for 'opacityVTable')
make: *** [build/lib3d.lo] Error 1


has this happened to any one else.....

if so.. how do you solve this:confused::confused:

---

### Post by subs on 2007-11-25
bump...

---

### Post by subs on 2007-11-25
anyone???

---

### Post by mmcev106 on 2007-11-29
Exact same problem here......

---

