---
title: "Skulltag"
date: 2010-06-07
forum: Gaming &amp; Leisure
---

### Post by jewfromdahood on 2010-06-07
Installed it version 98b
now it says 

./skulltag: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by ./skulltag)

---

### Post by denis153 on 2010-06-07
Are all your Direct X and drivers up to date?

---

### Post by Perfect Storm on 2010-06-07
Try symblink libgcc_s.so.1 into the skulltags lib folder. 
Do also 'ldd' the binary and post the output.

---

### Post by jewfromdahood on 2010-06-08
how do i do that?

---

### Post by Perfect Storm on 2010-06-09
ldd <path>/<binary>

sudo ln -s <path>/libgcc_s.so.1 <distination>/libgcc_s.so.1

---

### Post by perspectoff on 2010-08-14
I personally like the quick, simple instructions at

Ubuntuguide: [http://ubuntuguide.org/wiki/Ubuntu:All#Skulltag](http://ubuntuguide.org/wiki/Ubuntu:All#Skulltag)

Kubuntuguide: [http://kubuntuguide.org/All#Skulltag](http://kubuntuguide.org/All#Skulltag)

Dependencies require that the Universe repositories be enabled.

Make sure that is done and all your problems will likely disappear.

If you are compiling from scratch (not recommended), the make sure you have build-essential installed:

sudo apt-get install build-essential

---

