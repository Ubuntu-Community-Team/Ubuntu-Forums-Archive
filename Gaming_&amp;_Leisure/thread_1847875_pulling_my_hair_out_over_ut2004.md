---
title: "pulling my hair out over ut2004"
date: 2011-09-21
forum: Gaming &amp; Leisure
---

### Post by d.vanheeckeren on 2011-09-21
this is driving me nuts...I installed from original CDs, and have run into problem after problem, researching each until each problem was fixed.  Installed it, patched it, installed libstdc++5, resolved all dependencies, and now when trying to run, get the error:

```
error while loading shared libraries: ./libSDL-1.2.so.0: wrong ELF class: ELFCLASS64
```

and now I'm stuck...can't find anything else about this...I'm willing to research and piddle, but now I'm at my wit's end...after about 5 hours since I started this nightmare of the "native linux version of ut2004"....  hm....doesn't seem so native to me.  *LOL*

Thanks for any help anyone can provide.

-Daniel

---

### Post by Perfect Storm on 2011-09-21
ELF errors means wrong architecture of the library. You have to install libSDL-1.2.so.0 32-bit version to /usr/lib32/

If you have libsdl 32-bit library install under /usr/lib32/ under different name or different version, you need to create a symblink it to libSDL-1.2.so.0

---

### Post by HolgerB on 2011-09-22
Don't pull your hairs out !

Simply install UT2k4 as Windows version under WINE.

Works great and saves your hair....
:lolflag:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=5425](http://appdb.winehq.org/objectManager.php?sClass=version&iId=5425)

---

### Post by R33D3M33R on 2011-09-23
You could try and install ia32-libs (if you have 64-bit system).

---

### Post by Virus666 on 2011-09-25
If you are looking for UT2004's libSDL, here you are:

[http://ubuntuforums.org/showpost.php?p=2532915&postcount=5](http://ubuntuforums.org/showpost.php?p=2532915&postcount=5)

Just locate **libSDL-1.2.so.0** and **openal.so** to the game's **System** folder

---

