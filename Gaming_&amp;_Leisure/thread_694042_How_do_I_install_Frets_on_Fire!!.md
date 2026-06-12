---
title: "How do I install Frets on Fire?!?!?"
date: 2008-02-11
forum: Gaming &amp; Leisure
---

### Post by dragonblade on 2008-02-11
I downloaded FoF from sourceforge.com (Its supposed to be faster if u download it from sourceforge.com) but how do I install a tar.gz file? Please help me!
:guitar::guitar::guitar::guitar::guitar::guitar:
:guitar:

---

### Post by Vadi on 2008-02-11
I don't know about the speed and all, but installing a .tar.gz file is certainly more complicated then either

a) copy/pasting

```
sudo apt-get install fretsonfire
```

or 

b) Going to applications - add/remove, searching for "frets" checking it off, and clicking "Apply Changes"

Lemme know if you'll need help ;)

And remember this - add/remove, "sudo apt-get install", .debs (especially ones from getdeb.net) are a newbies friend, while "sources", .tar.gz, and .rpms aren't.

---

### Post by compiledkernel on 2008-02-11
[http://gaming.gwos.org/doku.php/guides:32bit:fretsonfire](http://gaming.gwos.org/doku.php/guides:32bit:fretsonfire)

---

### Post by dragonblade on 2008-02-11
Thx, I'll try this stuff out

---

### Post by banished_one on 2008-02-11
> **dragonblade said:**
> I downloaded FoF from sourceforge.com (Its supposed to be faster if u download it from sourceforge.com) but how do I install a tar.gz file? Please help me!
:guitar::guitar::guitar::guitar::guitar::guitar:
:guitar:

you have to extract it first then the common procedure is to run a 
./configure
make
make install

---

