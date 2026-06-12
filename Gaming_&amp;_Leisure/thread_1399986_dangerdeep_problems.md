---
title: "dangerdeep problems"
date: 2010-02-06
forum: Gaming &amp; Leisure
---

### Post by ubudog on 2010-02-06
Hi, I installed danger from the deep and when I try to run it, it says "dangerdeep: error while loading shared libraries: libSDL_mixer-1.2.so.0: cannot open shared object file: No such file or directory
"  I am using 32bit.  Any help?

---

### Post by ubudog on 2010-02-24
I fixed the previous problem by installing the libsdl libraries and such.  Now when I try to start a mission, it loads for about 3 seconds, then crashes with the following error message in the terminal:
SIGSEGV caught!
Stack trace: (16 frames)
0x8070202 in ./dangerdeep at ??:0
0x805d560 in ./dangerdeep at ??:0
0x274400 in [0x274400] at ??:0
0x817309f in ./dangerdeep at ??:0
0x81783b8 in ./dangerdeep at ??:0
0x8168efc in ./dangerdeep at ??:0
0x811ba70 in ./dangerdeep at ??:0
0x8162583 in ./dangerdeep at ??:0
0x805ee12 in ./dangerdeep at ??:0
0x80653f3 in ./dangerdeep at ??:0
0x8180257 in ./dangerdeep at ??:0
0x818be41 in ./dangerdeep at ??:0
0x8055a4f in ./dangerdeep at ??:0
0x8180257 in ./dangerdeep at ??:0
0x818be41 in ./dangerdeep at ??:0
0x8069e0c in ./dangerdeep at ??:0
Aborting program.
Aborted


Any help is appreciated.

---

