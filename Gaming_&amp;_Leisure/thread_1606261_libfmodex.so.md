---
title: "libfmodex.so"
date: 2010-10-26
forum: Gaming &amp; Leisure
---

### Post by Saronn on 2010-10-26
With a lot of games and programs, they don't work and in the terminal they output:


error while loading shared libraries: libfmodex.so: cannot open shared object file: No such file or directory

I'd like to fix it, and I've had the problem for a long time. I've also searched a lot for it, but I can't find a solution.

---

### Post by Perfect Storm on 2010-10-26
Here you are: [http://www.fmod.org/index.php/download#FMODExProgrammersAPI](http://www.fmod.org/index.php/download#FMODExProgrammersAPI)

---

### Post by Saronn on 2010-10-26
> **Artificial Intelligence said:**
> Here you are: [http://www.fmod.org/index.php/download#FMODExProgrammersAPI](http://www.fmod.org/index.php/download#FMODExProgrammersAPI)

I went into the directory and did sudo make install, and the output was


Installing FMOD Ex libraries and headers...
cp -f api/lib/libfmodex-4.33.04.so /usr/local/lib
cp -f api/lib/libfmodexL-4.33.04.so /usr/local/lib
ldconfig -n /usr/local/lib
mkdir -p /usr/local/include/fmodex
cp -f api/inc/*.h* /usr/local/include/fmodex
done.

it looks like it installed fine, but it didn't help.

---

### Post by Perfect Storm on 2010-10-26
symblink the current libfmodex-4.33.04.so with libfmodex.so

Note if you're using 32-bit apps in 64-bit OS that need this lib you need to put them in /usr/lib32
Also, In ubuntu the libs goes to /usr/lib

---

