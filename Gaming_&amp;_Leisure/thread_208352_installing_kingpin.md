---
title: "installing kingpin"
date: 2006-07-03
forum: Gaming &amp; Leisure
---

### Post by kariopto on 2006-07-03
Hi, I'm trying to install the game Kingpin, with the loki installer from [http://www.liflg.org/?catid=6&gameid=2](http://www.liflg.org/?catid=6&gameid=2)
I'm on an AMD64 computer using dapper-64bit.. 
I installed it as root, and when I try to run it it tells me it can't find libvga.so.1, libGL.so.0 and other libraries that i DO have.. 
Then i tried to install it with linux32, but it tells me:  error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

And i DO have libgtk-1.2.so.0!!!..
Any ideas?
Thanks in advance!

---

### Post by patrick295767 on 2006-07-04
I am also lookinf for this file  libvga.so.1

Did you install : 

apt-cache search vgalib-bin sthg ..?

---

### Post by patrick295767 on 2006-07-04
- Forget the alien via rpm

- trying : libvga.so.1
[http://www.svgalib.org/](http://www.svgalib.org/)
via make install can give: 
> ...
T6000_DRIVER_TEST -DINCLUDE_NEO_DRIVER -DINCLUDE_NEO_DRIVER_TEST -DINCLUDE_FBDEV                _DRIVER -c -o vga.o /root/svgalib-1.4.3/src/vga.c
/root/svgalib-1.4.3/src/vga.c:3919:1: pasting "." and "HDisplay" does not give a                 valid preprocessing token
/root/svgalib-1.4.3/src/vga.c:3920:1: pasting "." and "HSyncStart" does not give                 a valid preprocessing token
/root/svgalib-1.4.3/src/vga.c:3921:1: pasting "." and "HSyncEnd" does not give a                 valid preprocessing token
/root/svgalib-1.4.3/src/vga.c:3922:1: pasting "." and "HTotal" does not give a v                alid preprocessing token
/root/svgalib-1.4.3/src/vga.c:3923:1: pasting "." and "VDisplay" does not give a                 valid preprocessing token
/root/svgalib-1.4.3/src/vga.c:3924:1: pasting "." and "VSyncStart" does not give                 a valid preprocessing token
/root/svgalib-1.4.3/src/vga.c:3925:1: pasting "." and "VSyncEnd" does not give a                 valid preprocessing token
/root/svgalib-1.4.3/src/vga.c:3926:1: pasting "." and "VTotal" does not give a v                alid preprocessing token
/root/svgalib-1.4.3/src/vga.c:318: warning: 'release_acquire' defined but not us                ed
make[1]: *** [vga.o] Error 1
make[1]: Leaving directory `/root/svgalib-1.4.3/sharedlib'
make: *** [sharedlib/libvga.so.1.4.3] Error 2


- my recommanded way : 
I did, you need : 
> Unpacking **quake2** (from .../quake2_1%3a0.3-1.1ubuntu1_i386.deb) ...
Setting up **libsvga1** (1.4.3-22) ...
via apt-get 
to get the svga lib/ 
(I got my libvga.so.1)
 
- Concerning, for  libgtk-1.2.so.0, dont know yet.

---

### Post by FredB on 2006-07-04
It is gtk1.

---

