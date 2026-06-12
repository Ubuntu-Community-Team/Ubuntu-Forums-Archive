---
title: "Unreal Tournament on Ubuntu 12.04 x64 doesn't work"
date: 2012-08-03
forum: Gaming &amp; Leisure
---

### Post by Flow91 on 2012-08-03
Hello Ubuntu community

I've installed Ubuntu 12.04 64bits version. And I would like to play again to UT.

After installing it with ut-install-436-GOTY.run script with 'linux32 sh ....' 

When I tried to launch it, I have : 

> ./ut-bin: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory]And, when I make a symbolic link to the file, I have this :
> ./ut-bin: error while loading shared libraries: libX11.so.6: wrong ELF class: ELFCLASS64

Does anyone have succeded to resolved this problem (and to play to this good game)

Thank you.
Florent

---

### Post by Butthead on 2012-08-04
*Koff* Wine. :-\"

Easiest way, at least.  It installs all those annoying ia32 libraries and stuff you will need automatically for you. =;

---

### Post by Flow91 on 2012-08-05
Hello, 

Thanks for the reply.
I've installed the i386 libs

```
sudo apt-get install ia32-libs-sdl libc6-i386 lib32ncurses5 ia32-libs
```

 and it works !

---

