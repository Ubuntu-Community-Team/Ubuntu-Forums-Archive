---
title: "Gens for AMD64?"
date: 2007-10-30
forum: Gaming &amp; Leisure
---

### Post by nickdr on 2007-10-30
I tried to use this guide to install Gens on Ubuntu Gutsy AMD64.
[http://ubuntuforums.org/showthread.php?t=290008](http://ubuntuforums.org/showthread.php?t=290008)

However I get an error since I have 64 bit Gutsy. How do I install Gens/compile it. I already downloaded the latest from sourceforge.

Thanks!

---

### Post by GSZX1337 on 2008-02-13
You can try this:

> **roachk71 said:**
> 
```
dpkg --force-architecture -i *package_name*.deb
```Just make sure you have all of the 32-bit libraries needed by Gens installed first.


---

### Post by stevejesus on 2008-04-19
Forcing the arch makes Gens very unreliable.  It does alot of machine level stuff the 64 doesn't agree wth.

---

### Post by disturbedite on 2008-04-19
then compile it.

---

### Post by GSZX1337 on 2008-04-19
> **stevejesus said:**
> Forcing the arch makes Gens very unreliable.  It does alot of machine level stuff the 64 doesn't agree wth.

Gens works for me. Never had it crash.

---

### Post by jonthysell on 2008-05-15
I've just got gens 2.12b stable working on Gutsy 64bit:

Install ia32-libs if you haven't already:

```
sudo apt-get update
sudo apt-get install ia32-libs
```

Download gens stable from: [http://ubuntuforums.org/showthread.php?t=290008](http://ubuntuforums.org/showthread.php?t=290008)

Install with:

```
sudo dpkg --force-architecture -i gens_2.12b_i386.deb
```

If you're given icon errors (problem loading svg_loader.so), then follow: [http://ubuntuforums.org/showpost.php?p=4965707&postcount=9](http://ubuntuforums.org/showpost.php?p=4965707&postcount=9)

Be Happy!

---

### Post by Entity` on 2009-11-07
I am reviving this thread because this question is related.

Since a version of Gens is not out for 9.10, I just decided to compile it from scratch.  When I run ./configure, I get this line at the end:

```
configure: error: 64-bit is currently not supported.
```

Is there any way to force the installation?  I do have ia32-libs installed.

---

### Post by inukaze on 2011-01-17
> **Entity` said:**
> I am reviving this thread because this question is related.

Since a version of Gens is not out for 9.10, I just decided to compile it from scratch.  When I run ./configure, I get this line at the end:

```
configure: error: 64-bit is currently not supported.
```

Is there any way to force the installation?  I do have ia32-libs installed.

Well you can try with my Package

Gens AMD64 ( The Binary is 32 Bits )
[http://www.megaupload.com/?d=RFY8BCCP](http://www.megaupload.com/?d=RFY8BCCP)

you just need this for emulate Sega Genesis / Sega Master Drive

---

