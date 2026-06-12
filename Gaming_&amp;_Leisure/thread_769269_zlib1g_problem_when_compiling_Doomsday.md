---
title: "zlib1g problem when compiling Doomsday"
date: 2008-04-26
forum: Gaming &amp; Leisure
---

### Post by chibiusa255 on 2008-04-26
I'm trying to build Doomsday engine on Hardy and it keeps saying that zlib is not installed. I've grabbed zlib1g-dev from the repos and I still get the same thing. Any help would be appreciated. Keep in mind that I'm kinda a noob here ^_^

---

### Post by Perfect Storm on 2008-04-27
Well, a little more info is needed.
Attached the full terminal in/output.

---

### Post by chibiusa255 on 2008-04-27
Okies, here's the terminal output
```
chibiusa255@finalhaven:~/deng-1.9.0-beta5.1/doomsday/build/cmake$ cmake ../
-- Found PNG: /usr/lib/libpng.so
-- Looking for doxygen...
-- Looking for doxygen... - found /usr/bin/doxygen
-- Looking for dot tool...
-- Looking for dot tool... - found /usr/local/bin/dot
CMake Error: CPack package description file: "/home/chibiusa255/deng-1.9.0-beta5.1/doomsday/build/build/README" could not be found.
CMake Error: CPack license resource file: "/home/chibiusa255/deng-1.9.0-beta5.1/doomsday/build/engine/doc/LICENSE" could not be found.
CMake Error: ** zlib not found. On Ubuntu install zlib1g-dev. On Mac OSX install FIXME. On Windows install zlib123-dll.zip.
-- Configuring done
chibiusa255@finalhaven:~/deng-1.9.0-beta5.1/doomsday/build/cmake$ 

```

Thanks for the help ^_^

---

### Post by chibiusa255 on 2008-04-30
Any ideas, anyone?

---

### Post by Perfect Storm on 2008-04-30
I couldn't make it compiled. Have you tried with 0.7.0 if it will compile? If it do it might be something wrong with 0.7.6

---

### Post by MHaque on 2008-05-04
i am having the same problem.....I have installed the dev package and zlib.h is in my /usr/include folder but still I am getting the same error.....any clue....thanx for any support

---

### Post by Grishka on 2008-05-04
unpack beta5 first, then extract beta5.1 into the same folder, then compile with cmake. that worked for me.

---

### Post by disturbedite on 2008-05-04
just so you know, linux development of doomsday died a long time ago.  (the linux dev quit).  so i wouldn't hold my breath hoping it will be as good on linux as it is on other platforms.
(at the moment, it may be close, but as soon as development on a new version starts, the linux port will be left in the dust unless someone volunteers to be the linux maintainer/dev).

---

