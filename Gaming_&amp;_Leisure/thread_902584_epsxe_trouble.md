---
title: "epsxe trouble"
date: 2008-08-27
forum: Gaming &amp; Leisure
---

### Post by GrimmReaperVI on 2008-08-27
hi again guys. this time i've got a prob with setting up my epsxe (linux version)

the stupid thing wont' open!! i've clicked it again and again but nothing happens i've followed a tutorial to make a shell extenstion in usr/local/sbin which reads:

```
#!/bin/bash

export EPSXE='/media/Storage/epsxe'
export LD_LIBRARY_PATH=$EPSXE
cd $EPSXE
./epsxe
chmod 666 $EPSXE/cfg/*.cfg $EPSXE/sstates/* \
$EPSXE/memcards/*.mcr $EPSXE/snap/* 2>/dev/null
```

storage is th name of my drive in which i keep all my stuff :lolflag: 

anyway 

```
daniel@daniel-desktop:~$ start_epsxe.sh
./epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
```


the tutorial said i needed libpthread.so.0 or something to avoid graphical errors. so i used

```
cp /lib/libpthread.so.0 $EPSXE/ 
```


help is much appreciated

---

### Post by DoktorSeven on 2008-08-27
Search for GTK version 1.2 in Synaptic, you'll need to download and install that library for it to work.

---

### Post by GrimmReaperVI on 2008-08-28
It doesn't exist in the synaptic :( mind giving me a code for it?

---

### Post by Perfect Storm on 2008-08-28
libgtk l.2 Just search libgtk

---

### Post by GrimmReaperVI on 2008-08-28
ok i found it! And i installed it...and epsxe still ain't working



```
daniel@daniel-desktop:~$ start_epsxe.sh
./epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

```

---

### Post by Perfect Storm on 2008-08-28
Are you using Ubuntu 64-bit?

---

### Post by GrimmReaperVI on 2008-08-29
nope :)
just the normal one

-edit- Ah got it. I don't have most of the packages for it to play e.g libthread...whatever that is


--further edit--
what should i search for if i want to find libstdc++.so.5 ?
And libgpu.so

---

### Post by wingnux on 2008-08-29
"sudo apt-get install getlibs"

Then use: getlibs -32 'name of the lib the program is asking for' 
(ie. getlibs -32 libstdc++.so.5)

---

### Post by GrimmReaperVI on 2008-08-29
Ok guys I almost figured it out. Now I just need a lib or 2

```
libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
```

```
plugins/libgpu.so: cannot open shared object file: No such file or directory
```

Can someone tell me where to find these?

---

