---
title: "UT opengl renderer for Linux"
date: 2005-11-14
forum: Gaming &amp; Leisure
---

### Post by BLTicklemonster on 2005-11-14
Is there anyone who is making improvements to the oglrender for UT like Chris Dohnal does for windows?
[http://cwdohnal.home.mindspring.com/utglr/](http://cwdohnal.home.mindspring.com/utglr/)


He does have information limitedly:

> Linux builds
I never seem to hear any good news about attempts to build the updated renderer on Linux. Unfortunately, I can only provide limited help in this area. I do try to keep the code cross platform friendly, but it's unlikely that I will be able to attempt to build it on other platforms anytime in the near future. I know the current code won't compile as is with gcc, but I expect that only minor syntax fixups and basic non-essential feature removal will be able to make the updates I added both compile cleanly and work correctly.

The first major step in attempting to build the updated renderer on Linux is to make sure you can build the original renderer code before I added any updates to it. This will ensure that there are not any major existing issues before going forward and attempting to use the new code. If any problems are encountered in this stage, it's not really anything I can help with much because I don't have a local build environment for this platform, didn't write this code, etc. If there's some problem like maybe the ut432 header files don't quite match the current Linux version of UT and cause problems because of this, that falls into the I didn't break it and I can't fix it category.

You'll need to use a compatible version of gcc. Unfortunately, ABI changes mean you will almost certainly not be able to use a newer version of gcc (unless the rest of the game were compiled with it of course).

You can easily ifdef out the SSE code I added because whatever compiler you use probably won't support it. This is not a major loss since the SSE code I added only provides very minor speedups.

There's a chance there will be problems with the sstream code I used for the debug stream when using an older gcc and/or older libraries. Although it requires numerous changes to remove it, this code is non-essential, and the changes should be simple.

There are good reasons to try to get an updated renderer working on Linux if running UT natively here. Besides just being very obsolete at this point, the original OpenGL renderer code does contain a couple of more major design/implementation issues that would be good to have fixed.


Is anyone in the linux community experienced with opengl enough that they are doing anything like this? Where can I get and updated one if so?

---

### Post by slux on 2005-11-14
[Ryan "Icculus" Gordon]("http://icculus.org/cgi-bin/finger/finger.pl?user=icculus") and the [UTPG]("http://www.utpg.org/") might be interested. I remember reading in Icculus' plan earlier that he thought the game needs a renderer rewrite.

---

### Post by Zeroedout on 2005-11-16
Hi, i was not aware of UTPG, so i thought i'de download and install it. Now i get this error ```
Assertion failed: GetPropertiesSize()>=sizeof(UObject) [File:UnClass.cpp] [Line: 1032]

History:

Exiting due to error
```

Anyone know how I can fix it?

---

### Post by BLTicklemonster on 2005-11-16
Oooh, you don't need either of them. 436 is all you need. 441 doesn't do much for a client, and 451 is for servers. If you can uninstall whatever you did, do it.

---

