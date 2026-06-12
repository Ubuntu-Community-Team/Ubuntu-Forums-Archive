---
title: "Usplash Help"
date: 2009-03-19
forum: Desktop Environments
---

### Post by smith3 on 2009-03-19
I need to make a custom usplash page- even if it is just removing all the graphics except the loading bar.

Ubuntu (8.04) Gnome 2.22.3

I have looked at some usplash themes but the do not seem to compile correctly for me (see previous posts about noobieness).

I tried this one out (it seemed recent enough to be good with my distribution):

[\http://www.gnome-look.org/content/show.php/ubuntu-Bar-only?content=99843 ]("http://www.gnome-look.org/content/show.php/ubuntu-bar-only?content=99843")

 but get errors:

[FONT="Fixedsys"]computername:~/Public/usplash testing/nobar/ubuntu-bar-only$ sudo make
make: Circular throbber_back.png <- throbber_back.png.c dependency dropped.
pngtousplash throbber_back.png > throbber_back.png.c
gcc  -g -Wall -fPIC -o throbber_back.png.c.o -c throbber_back.png.c
In file included from throbber_back.png.c:2:
/usr/include/usplash-theme.h:24:23: error: sys/types.h: No such file or directory
/usr/include/usplash-theme.h:25:20: error: stdlib.h: No such file or directory
In file included from throbber_back.png.c:2:
/usr/include/usplash-theme.h:77: error: expected declaration specifiers or â€˜...â€™ before â€˜size_tâ€™
/usr/include/usplash-theme.h:79: error: expected declaration specifiers or â€˜...â€™ before â€˜size_tâ€™
/usr/include/usplash-theme.h:93: error: expected specifier-qualifier-list before â€˜u_int32_tâ€™
make: *** [throbber_back.png.c.o] Error 1
rm throbber_back.png.c
computername:~/Public/usplash testing/nobar/ubuntu-bar-only$ [/FONT]

I tried to decipher this a bit and it looks like i may not have all the proper files for compiling on my computer, but am at a loss on how to proceed.
I have very little experience with make files and compiling. Maybe I just have something in wrong spot or such. Thanks a lot.

---

### Post by smith3 on 2009-03-20
[FONT="Fixedsys"]sudo apt-get install libbogl-dev [/FONT]

gets rid of errors

---

