---
title: "Make Error????"
date: 2005-12-26
forum: General Help
---

### Post by ephman on 2005-12-26
hi,

i'm having a real tough time trying to install this nw802 video driver for my dark ring logitech quickcam.  this is the output for when i make (ha ha ha).  any ideas how i can fix this???


root@wintermute:/home/ephman/nw802-2.4/nw802-2.4# make
ln -sf /lib/modules/`uname -r`/build/drivers/usb/media/usbvideo.h .
ln -sf /lib/modules/`uname -r`/build/drivers/usb/media/usbvideo.c .
make -C /lib/modules/`uname -r`/build SUBDIRS=`pwd` modules
make[1]: Entering directory `/lib/modules/2.6.12-10-686/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.12-10-686/build'
make: *** [default] Error 2
root@wintermute:/home/ephman/nw802-2.4/nw802-2.4#


thanks for the bandwidth,
ephman

---

### Post by odin on 2005-12-27
Sorry if this sounds stupid but It's just to be sure you have done it.Is there a configure file in the tarball you downloaded?

Some times there is adn then you have to execute:

./configure and then
make 
make install

you probably know this but....I also  sugest to read the README you should have,it helps many times.

---

### Post by ephman on 2005-12-27
hi,

thank you.  i wish it was that easy.  but i've been searching and posting in many places and so far no help.  i'm getting close to just buying a new webcam.  too bad it's a perfectly good camera.

thanks,
ephman

---

### Post by Lambert on 2005-12-27
Have you followed these instructions to patch for 2.6 kernel?

New files in the CVS.
    Patch for kernel 2.6 and a Makefile for 2.6. And some small bugg fixes.
   So to compile with a 2.6 kernel :

```
cvs -d:pserver:anonymous@cvs.nw802.sourceforge.net:/cvsroot/nw802 login
cvs -z3 -d:pserver:anonymous@cvs.nw802.sourceforge.net:/cvsroot/nw802
co nw802-2.4
cd nw802-2.4
cp Makefile.26 Makefile
patch -p0 < patch-2.6
make clean
make
```

The source forge project shows latest news from Dec 2004 and this comes from June 2004 so not sure if it's the latest.

---

### Post by ephman on 2005-12-27
yup i applied the patch seemed to work fine.  

thanks,
ephman

---

### Post by Zwack on 2005-12-27
It seems that it's trying to compile some modules in /lib/modules/...  Do you have the Linux source installed for your version?  That may be what it's looking for.  

If you need to install the source then make sure you run .configure again.

I hope that this helps,

Z.

---

### Post by ephman on 2005-12-27
thank you, i tried that already, infact i also loaded the kernel's headers.  nope still no go...

thanks,
ephman

---

