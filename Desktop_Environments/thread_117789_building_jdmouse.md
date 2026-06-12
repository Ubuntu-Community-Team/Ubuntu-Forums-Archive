---
title: "building jdmouse"
date: 2006-01-15
forum: Desktop Environments
---

### Post by jackinloadup on 2006-01-15
im having problems when i try to "make" jdmouse. i have tryed repededly to figure it out unsucessfuly. anyhelp would be great. im running breezy on a vaio. thz 

user:~/Desktop/jdmouse-gtk-0.1$ make
make -C src all
make[1]: Entering directory `/home/user/Desktop/jdmouse-gtk-0.1/src'
cc -O2 `gtk-config --cflags` jdmouse.c -o jdmouse `gtk-config --libs` && strip jdmouse
jdmouse.c: In function ‘soundvolume_adjuster’:
jdmouse.c:712: error: syntax error before string constant
jdmouse.c: In function ‘backlight_adjuster’:
jdmouse.c:753: error: syntax error before string constant
jdmouse.c: In function ‘backlight_toggle’:
jdmouse.c:783: error: syntax error before string constant
jdmouse.c: In function ‘main’:
jdmouse.c:983: warning: incompatible implicit declaration of built-in function ‘exit’
jdmouse.c:992: warning: incompatible implicit declaration of built-in function ‘exit’
jdmouse.c:997: warning: incompatible implicit declaration of built-in function ‘exit’
jdmouse.c:1007: warning: incompatible implicit declaration of built-in function ‘exit’
make[1]: *** [jdmouse] Error 1
make[1]: Leaving directory `/home/user/Desktop/jdmouse-gtk-0.1/src'
make: *** [all] Error 2

---

### Post by jackinloadup on 2006-01-22
is there no one that has had this problem? am i missing any make files?

---

