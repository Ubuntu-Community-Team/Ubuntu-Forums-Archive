---
title: "scpa5xx drivers for webcam"
date: 2005-05-24
forum: Desktop Environments
---

### Post by frs-design on 2005-05-24
Hello,

I'm using kubuntu for 2 months and i find it very good.

I have got one problem installing the spca5xx drivers for my webcam which seems to be supported: Mustek DV4000.

I have found a pretty cool tutorial here: [http://www.ubuntulinux.org/wiki/Spca5xx](http://www.ubuntulinux.org/wiki/Spca5xx)

But i can't link anything using the following lines:

ln -s /usr/src/linux-source-`uname -r`/debian/build/build-<arch> /lib/modules/`uname -r`/build
or ln -s /usr/src/linux-source-2.6.10-5-386/debian/build/build-386 /lib/modules/2.6.10-5-386/build
or ln -s /usr/src/linux-source-2.6.10/debian/build/build-386 /lib/modules/2.6.10-5-386/build

In fact, i have installed linux-source-2.6.10, because my kernel (uname -r) is 2.6.10-5-386
That gaves me a tar.bz2 file called linux-source-2.6.10.tar.bz2 in /usr/src/
I uncompressed it and i got the directory called /usr/src/linux-source-2.6.10

But I DON'T HAVE A SUB-DIRECTORY called /usr/src/linux-source-2.6.10/debian/build/build-386 needed to create the link !!!

somebody can help me please ???

Bye ++

---

### Post by madamore on 2005-06-02
I´m not sure about it, but I think you have to intall the "kernel header" from the repository. Then you will have the kernel source to compile kernell drivers.
I did it with my logitel express cam, and works nice.

---

### Post by frs-design on 2005-06-02
Yes that's right, that's what i did and it works now !

@+

---

