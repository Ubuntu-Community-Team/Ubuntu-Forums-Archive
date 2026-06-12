---
title: "[SOLVED] ristretto and thunar-vfs"
date: 2007-11-09
forum: Debian
---

### Post by ZipoTe on 2007-11-09
Hello folks!

I'm using Debian Testing with xfce desktop and trying to install ristretto 0.0.11 to browse my photos :P (it's a picture-viewer) but i can't compile it. It says i need thunar-vfs and i don't know what to do. I "googled", searched the forums... but nothing:cry: 

So, anyone can help?

Thank you!!

---

### Post by benuski on 2007-11-09
I would try installing libthunar-vfs-1-2 and libthunar-vfs-1-dev and then trying to recompile it.

---

### Post by ZipoTe on 2007-11-12
thank you! that was it!! :guitar: but now, when i recompile, i have a problem during make:

```
make[2]: se sale del directorio `/home/dani/Desktop/ristretto-0.0.11/src'
Making all in po
make[2]: se ingresa al directorio `/home/dani/Desktop/ristretto-0.0.11/po'
file=`echo cs | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file cs.po
/bin/sh: line 1: -o: command not found
make[2]: *** [cs.gmo] Error 127
make[2]: se sale del directorio `/home/dani/Desktop/ristretto-0.0.11/po'
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio `/home/dani/Desktop/ristretto-0.0.11'
make: *** [all] Error 2

```

so... someone knows what to do?:confused:

---

### Post by ZipoTe on 2007-11-14
I'm reading the make documentation from GNU project but i can't find this error in the documentation :(

some help would be apreciated ;)

---

### Post by ZipoTe on 2007-11-15
after lots of reading, googling and translating from polish and german to english i solved the problem:

sudo apt-get install po-debconf


hope it helps:guitar:

---

### Post by siafok on 2007-12-12
I know it is old treat but you help me with above post so I want to thank you.

---

