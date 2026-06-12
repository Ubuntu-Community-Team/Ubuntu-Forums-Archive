---
title: "Apxs for apache ..."
date: 2005-10-15
forum: Desktop Environments
---

### Post by dbee on 2005-10-15
Why can't my apxs function find the mod_security.c it needs to include the module on my apache DSO install.

The mod_sec manual says that apxs will find it 'anywhere', which seems a little strange 

Will it find it on my porno usb, that I keep hidden in my backpack at the back of the wardrobe in the spare room ???? 
... I'm guessing that it won't :D 

but anyway back to my point ... when I type

apxs -cia mod_security.c 

I get 

/usr/local/apache2/build/libtool --silent --mode=compile gcc -prefer-pic  -DAP_HAVE_DESIGNATED_INITIALIZER -DLINUX=2 -D_REENTRANT -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -D_SVID_SOURCE -D_GNU_SOURCE -g -O2 -pthread -I/usr/local/apache2/include  -I/usr/local/apache2/include   -I/usr/local/apache2/include   -c -o mod_security.lo mod_security.c && touch mod_security.slo
gcc: mod_security.c: No such file or directory
gcc: no input files
apxs:Error: Command failed with rc=65536
.
 
I've copied mod_security.c to various folders around the apache installation but it can't seem to find any of them :confused:

---

### Post by dbee on 2005-10-15
No, it's ok now,

For some reason my system changed the .c to .loT when it moved it to the bin folder of the apache installation 

It works fine as mod_sec*.c

---

