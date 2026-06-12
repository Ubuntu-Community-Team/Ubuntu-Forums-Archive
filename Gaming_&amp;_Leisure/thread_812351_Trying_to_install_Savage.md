---
title: "Trying to install Savage"
date: 2008-05-29
forum: Gaming &amp; Leisure
---

### Post by webcoded612 on 2008-05-29
Ok so I'm trying to install Savage.  I downloaded the run file, executed it, and this is what I get:  

```
Verifying archive integrity... All good.
Uncompressing Savage and SEP3T Installer..........................................................
/home/james/.setup8705: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

```

Dunno what this all means. Specs are:

2.0Ghz AMD Athalon64 (running 32 bit Ubuntu Hardy Heron)
1.5Gb RAM
80Gb HDD
ATI Radeon X1300 PCI-E 256MB video.  

I'm using the restricted driver because I've read all the nightmare stories about trying to get the junk from ATI to work.  Could this be the prob?  I'm still kind of a Linux noob, so I don't even know where to start looking.  

Any help would be greatly appreciated.  

Thanks!

---

### Post by corbbz on 2008-05-30
You are missing some old libraries.
Try installing 'libgtk1.2' from Synaptic Package Manager.

Or the same from console:
```
sudo apt-get install libgtk1.2
```

Hope it helps!

---

### Post by Perfect Storm on 2008-05-30
> libgtk-1.2.so.0: cannot open shared object file: No such file or directory

Open Synaptic search for libgtk1.2 and install it.

or
```
sudo apt-get install libgtk1.2
```

But I doubt it works with ATI card.
guide: [http://gaming.gwos.org/doku.php/guides:64bit:savage_1](http://gaming.gwos.org/doku.php/guides:64bit:savage_1)
(if you're not using 64-bit - the part where it says "install ia32-libs" is not needed).

---

