---
title: "need help with NGplant install"
date: 2009-01-02
forum: General Help
---

### Post by zippyties on 2009-01-02
I am very new to linux, and not at all proficient when it comes to the CLI.

I am trying to install [[COLOR="RoyalBlue"]ngplant[/COLOR]]("http://ngplant.sourceforge.net/"), and I have found a website with [[COLOR="RoyalBlue"][COLOR="RoyalBlue"]instructions[/COLOR][/COLOR]]("http://www.opendimension.org/blender_en/ngplant_from_source.php") on how to install in linux.  However I have been hitting a snag when it comes to the SCONS command it always returns the following dialog;

::LoadImageData(P3DImageData*, const char*, const char*) const’:
ngput/p3dimage.cpp:371: error: ‘strcmp’ was not declared in this scope
scons: *** [ngput/p3dimage.o] Error 1
scons: building terminated because of errors.

There has been some talk of needing "WXWidgets" for this problem, so I installed the latest version from the synaptic manager.

My question is this; Am I having this problem because of user error?  Or is it something else?  Any help would be greatly appriciated.

Thanks,

---

### Post by BenAshton24 on 2009-01-02
I followed the instructions precisely and got the same error... My suggestion is to install as many WxWidget libraries from synaptic as possible and keep trying! it will work eventually... or at least try and convince yourself of that XD

Hope this helps... Even though it probably won't

Ben

---

### Post by Gaming4JC on 2009-01-21
Currently, I find it impossible to compile. It needs many headers added. Once you fix the first bug you mentioned there is at least a dozen more, and I still haven't gotten any success. :(

You need the following headers added to each file:
p3dimage.cpp --- add #include <string.h>
p3dospath.cpp --- add #include <cstring> (or <string.h>)

Once you get that done you should get this:
```

LEW_STATIC=1 -Ingpshot -I. -Iextern/glew/include ngpshot/p3dshaders.cpp
ngpshot/p3dshaders.cpp: In function ‘void DumpInfoLog(GLhandleARB)’:
ngpshot/p3dshaders.cpp:82: error: ‘malloc’ was not declared in this scope
ngpshot/p3dshaders.cpp:99: error: ‘stderr’ was not declared in this scope
ngpshot/p3dshaders.cpp:99: error: ‘fprintf’ was not declared in this scope
ngpshot/p3dshaders.cpp:102: error: ‘free’ was not declared in this scope
ngpshot/p3dshaders.cpp:106: error: ‘stderr’ was not declared in this scope
ngpshot/p3dshaders.cpp:106: error: ‘fprintf’ was not declared in this scope
ngpshot/p3dshaders.cpp: In function ‘bool CompileShaderObject(GLhandleARB*, GLenum, GLsizei, const GLcharARB**)’:
ngpshot/p3dshaders.cpp:159: error: ‘stderr’ was not declared in this scope
ngpshot/p3dshaders.cpp:159: error: ‘fprintf’ was not declared in this scope
ngpshot/p3dshaders.cpp: In member function ‘GLhandleARB P3DShaderLoader::GetProgramHandle(bool, bool, bool) const’:
ngpshot/p3dshaders.cpp:322: error: ‘stderr’ was not declared in this scope
ngpshot/p3dshaders.cpp:322: error: ‘fprintf’ was not declared in this scope
ngpshot/p3dshaders.cpp:346: error: ‘stderr’ was not declared in this scope
ngpshot/p3dshaders.cpp:346: error: ‘fprintf’ was not declared in this scope
scons: *** [ngpshot/p3dshaders.o] Error 1
scons: building terminated because of errors.

```

(03:50:34 PM) james_w: malloc is stdlib.h
(03:51:15 PM) james_w: stderr is stdio.h

(sadly it doesnt work by adding those headers... but thanks to james_w for the two fixes). :D

---

### Post by Gaming4JC on 2009-01-21
With help from _16aR_ a MOTU, I was able to compile it. Many thanks to him.

to ngpview.cpp add:
```

#include <stdio.h>
#include <stdlib.h>

```

and to p3dshader.cpp add:
```

#include <cstdio>
#include <malloc.h>
#include <vector>

#include <ngput/p3dglext.h>

#include <p3dshaders.h>
using namespace std;

```

You should then be able to compile a generic linux binary! :D

If I can figure out how I might make a deb

---

### Post by Gaming4JC on 2009-01-21
:popcorn:
If you want to try the generic linux build, here it is:
[http://www.mediafire.com/?vzcngcyib9g](http://www.mediafire.com/?vzcngcyib9g)

---

### Post by charlescva on 2009-02-02
The following patch needs to be applied to the ngPlant source before it can be compiled.

[http://aur.archlinux.org/packages/ngplant/ngplant/gcc43.patch]("http://aur.archlinux.org/packages/ngplant/ngplant/gcc43.patch")

---

### Post by SlowButDim on 2009-02-21
I added the patch info to the compile page. Sorry for misguiding tutorial :(

[http://opendimension.org/blender_en/ngplant_from_source.php](http://opendimension.org/blender_en/ngplant_from_source.php)

---

### Post by onnod on 2009-12-19
I followed the [tutorial]("http://opendimension.org/blender_en/ngplant_from_source.php") and applied the patch, but upon executing scons got this error:

```
scons: warning: The BoolOption() function is deprecated; use the BoolVariable() function instead.
File "/home/donno/Downloads/ngplant-0.9.7/SConstruct", line 19, in <module>
Checking for c++ compiler presence... (cached) yes
Checking for __attribute__((unused)) support presence in g++... yes
Checking for C++ header file stdint.h... yes
Checking for C header file Python.h... no
Python.h not found... _ngp (Python bindings) will not be built
Checking unsigned int type sizeof ... 
Checking unsigned int* type sizeof ... 
Checking endianess ... 
Checking for C function sincosf()... no
Checking for C++ function sincosf()... yes
Checking for C function roundf()... no
Checking for C++ function roundf()... yes
Checking for C++ header file GL/glut.h... no
glut library not found - ngpview application will not be built
Checking GLEW presence and usability ... no
No installed glew library found - using internal GLEW sources...
Checking for xsltproc command... (cached) yes
Checking for lua-config command... (cached) no
No installed Lua libraries found. Using internal Lua sources...

scons: warning: The env.Copy() method is deprecated; use the env.Clone() method instead.
File "/home/donno/Downloads/ngplant-0.9.7/ngpcore/SConscript", line 27, in <module>
scons: done reading SConscript files.
scons: Building targets ...
g++ -o ngpcore/p3dmath.o -c -W -Wall -O3 --fast-math -DHAVE_GXX_ARG_ATTR_UNUSED -DHAVE_STDINT_H -DUINTSIZE= -DUINTPTRSIZE= -DHAVE_SINCOSF -DHAVE_ROUNDF -DGLEW_STATIC=1 -I. ngpcore/p3dmath.cpp
g++ -o ngpcore/p3dmathrng.o -c -W -Wall -O3 --fast-math -DHAVE_GXX_ARG_ATTR_UNUSED -DHAVE_STDINT_H -DUINTSIZE= -DUINTPTRSIZE= -DHAVE_SINCOSF -DHAVE_ROUNDF -DGLEW_STATIC=1 -I. ngpcore/p3dmathrng.cpp
g++ -o ngpcore/p3dmathspline.o -c -W -Wall -O3 --fast-math -DHAVE_GXX_ARG_ATTR_UNUSED -DHAVE_STDINT_H -DUINTSIZE= -DUINTPTRSIZE= -DHAVE_SINCOSF -DHAVE_ROUNDF -DGLEW_STATIC=1 -I. ngpcore/p3dmathspline.cpp
g++ -o ngpcore/p3dplant.o -c -W -Wall -O3 --fast-math -DHAVE_GXX_ARG_ATTR_UNUSED -DHAVE_STDINT_H -DUINTSIZE= -DUINTPTRSIZE= -DHAVE_SINCOSF -DHAVE_ROUNDF -DGLEW_STATIC=1 -I. ngpcore/p3dplant.cpp
In file included from ngpcore/p3dplant.cpp:32:
/usr/include/stdlib.h:33:20: error: stddef.h: No such file or directory
In file included from ngpcore/p3dplant.cpp:32:
/usr/include/stdlib.h:140: error: &#8216;size_t&#8217; does not name a type
In file included from ngpcore/p3dplant.cpp:32:
/usr/include/stdlib.h: In function &#8216;double atof(const char*)&#8217;:
/usr/include/stdlib.h:281: error: &#8216;NULL&#8217; was not declared in this scope
/usr/include/stdlib.h: In function &#8216;int atoi(const char*)&#8217;:
/usr/include/stdlib.h:286: error: &#8216;NULL&#8217; was not declared in this scope
/usr/include/stdlib.h: In function &#8216;long int atol(const char*)&#8217;:
/usr/include/stdlib.h:291: error: &#8216;NULL&#8217; was not declared in this scope
/usr/include/stdlib.h: In function &#8216;long long int atoll(const char*)&#8217;:
/usr/include/stdlib.h:300: error: &#8216;NULL&#8217; was not declared in this scope
In file included from ngpcore/p3dplant.cpp:32:
/usr/include/stdlib.h: At global scope:
/usr/include/stdlib.h:337: error: &#8216;size_t&#8217; has not been declared
/usr/include/stdlib.h:367: error: &#8216;size_t&#8217; has not been declared
/usr/include/stdlib.h:471: error: &#8216;size_t&#8217; was not declared in this scope
/usr/include/stdlib.h:471: error: expected &#8216;,&#8217; or &#8216;;&#8217; before &#8216;throw&#8217;
/usr/include/stdlib.h:473: error: &#8216;size_t&#8217; was not declared in this scope
/usr/include/stdlib.h:473: error: &#8216;size_t&#8217; was not declared in this scope
/usr/include/stdlib.h:473: error: initializer expression list treated as compound expression
/usr/include/stdlib.h:474: error: expected &#8216;,&#8217; or &#8216;;&#8217; before &#8216;throw&#8217;
/usr/include/stdlib.h:485: error: &#8216;size_t&#8217; has not been declared
In file included from /usr/include/stdlib.h:497,
                 from ngpcore/p3dplant.cpp:32:
/usr/include/alloca.h:33: error: &#8216;size_t&#8217; was not declared in this scope
/usr/include/alloca.h:33: error: expected &#8216;,&#8217; or &#8216;;&#8217; before &#8216;throw&#8217;
In file included from ngpcore/p3dplant.cpp:32:
/usr/include/stdlib.h:502: error: &#8216;size_t&#8217; was not declared in this scope
/usr/include/stdlib.h:502: error: expected &#8216;,&#8217; or &#8216;;&#8217; before &#8216;throw&#8217;
/usr/include/stdlib.h:507: error: &#8216;size_t&#8217; has not been declared
/usr/include/stdlib.h:507: error: &#8216;size_t&#8217; has not been declared
/usr/include/stdlib.h:705: error: &#8216;size_t&#8217; has not been declared
/usr/include/stdlib.h:705: error: &#8216;size_t&#8217; has not been declared
/usr/include/stdlib.h:710: error: &#8216;size_t&#8217; has not been declared
/usr/include/stdlib.h:710: error: &#8216;size_t&#8217; has not been declared
/usr/include/stdlib.h:713: error: &#8216;size_t&#8217; has not been declared
/usr/include/stdlib.h:713: error: &#8216;size_t&#8217; has not been declared
/usr/include/stdlib.h:788: error: &#8216;size_t&#8217; has not been declared
/usr/include/stdlib.h:791: error: &#8216;size_t&#8217; has not been declared
/usr/include/stdlib.h:795: error: &#8216;size_t&#8217; has not been declared
/usr/include/stdlib.h:799: error: &#8216;size_t&#8217; has not been declared
/usr/include/stdlib.h:808: error: &#8216;size_t&#8217; has not been declared
/usr/include/stdlib.h:812: error: &#8216;size_t&#8217; has not been declared
/usr/include/stdlib.h:819: error: &#8216;size_t&#8217; does not name a type
/usr/include/stdlib.h:822: error: &#8216;size_t&#8217; does not name a type
/usr/include/stdlib.h:885: error: &#8216;size_t&#8217; has not been declared
In file included from /usr/include/stdlib.h:903,
                 from ngpcore/p3dplant.cpp:32:
/usr/include/bits/stdlib.h:26: error: &#8216;size_t&#8217; has not been declared
/usr/include/bits/stdlib.h:30: error: &#8216;size_t&#8217; has not been declared
/usr/include/bits/stdlib.h: In function &#8216;char* realpath(const char*, char*)&#8217;:
/usr/include/bits/stdlib.h:40: error: &#8216;size_t&#8217; was not declared in this scope
/usr/include/bits/stdlib.h: At global scope:
/usr/include/bits/stdlib.h:53: error: &#8216;size_t&#8217; has not been declared
/usr/include/bits/stdlib.h:54: error: &#8216;size_t&#8217; has not been declared
/usr/include/bits/stdlib.h:55: error: &#8216;size_t&#8217; has not been declared
/usr/include/bits/stdlib.h:58: error: &#8216;size_t&#8217; has not been declared
/usr/include/bits/stdlib.h:58: error: &#8216;size_t&#8217; has not been declared
/usr/include/bits/stdlib.h:65: error: &#8216;size_t&#8217; has not been declared
/usr/include/bits/stdlib.h: In function &#8216;int ptsname_r(int, char*, int)&#8217;:
/usr/include/bits/stdlib.h:67: error: &#8216;size_t&#8217; was not declared in this scope
/usr/include/bits/stdlib.h: At global scope:
/usr/include/bits/stdlib.h:78: error: &#8216;size_t&#8217; has not been declared
/usr/include/bits/stdlib.h: In function &#8216;int wctomb(char*, wchar_t)&#8217;:
/usr/include/bits/stdlib.h:93: error: &#8216;size_t&#8217; was not declared in this scope
/usr/include/bits/stdlib.h: At global scope:
/usr/include/bits/stdlib.h:99: error: &#8216;size_t&#8217; does not name a type
/usr/include/bits/stdlib.h:102: error: &#8216;size_t&#8217; does not name a type
/usr/include/bits/stdlib.h:106: error: &#8216;size_t&#8217; does not name a type
/usr/include/bits/stdlib.h:113: error: &#8216;size_t&#8217; does not name a type
/usr/include/bits/stdlib.h:131: error: &#8216;size_t&#8217; does not name a type
/usr/include/bits/stdlib.h:134: error: &#8216;size_t&#8217; does not name a type
/usr/include/bits/stdlib.h:138: error: &#8216;size_t&#8217; does not name a type
/usr/include/bits/stdlib.h:144: error: &#8216;size_t&#8217; does not name a type
scons: *** [ngpcore/p3dplant.o] Error 1
scons: building terminated because of errors.
zsh: exit 2     scons
```

Ubuntu 9.10

---

