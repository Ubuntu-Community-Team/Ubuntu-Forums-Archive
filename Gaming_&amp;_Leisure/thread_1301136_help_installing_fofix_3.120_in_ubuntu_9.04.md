---
title: "help installing fofix 3.120 in ubuntu 9.04"
date: 2009-10-25
forum: Gaming &amp; Leisure
---

### Post by glenuk on 2009-10-25
i'm trying to install fofix 3.120 from a .tar.gz file i get as far as the ./configure part & it says
 "bash: ./configure: No such file or directory"
i've extracted the .tar.gz file to my home folder 
is there anything i'm missing to be able to get this to install?
thanks 
glen

---

### Post by doorknob60 on 2009-10-25
Did you cd into the right directory? Also, I don't think you need to run configure, try running "make dist" I don't know if this will help you, but I'll link you to my PKGBUILD on the Arch AUR. Not very useful in Ubuntu, but if you read the PKGBUILD file, it might give you some hints on how to install it. Also on the page it has a patch for the makefile that you might need for it to correctly compile. [http://aur.archlinux.org/packages.php?ID=20454](http://aur.archlinux.org/packages.php?ID=20454)

---

### Post by glenuk on 2009-10-25
on doing the cd command the line says "penguin@penguin-desktop:~/fofix-3.120$" so i'm guessing its pointing to the right place
thanks
glen

---

### Post by doorknob60 on 2009-10-25
Yeah that should be right. Did you try running this?
```
make dist
```

---

### Post by glenuk on 2009-10-25
i just tried that and i got this:

/bin/sh: svn: not found
--- Detected version: 3.120~
--- Building binary
cxfreeze --target-dir dist \
--exclude-modules tcl,tk,Tkinter \
--include-modules \
encodings.string_escape,\
encodings.iso8859_1,\
SongChoosingScene,\
GuitarScene,\
ctypes.util,pkg_resources,weakref,Image,\
OpenGL,OpenGL.platform.glx,OpenGL.arrays.ctypesarrays,OpenGL.arrays.numpymodule,OpenGL.arrays.lists,OpenGL.arrays.numbers,OpenGL.arrays.strings,\
xml.sax.drivers2.drv_pyexpat,\
GameResultsScene src/FoFiX.py
make: cxfreeze: Command not found
make: *** [dist] Error 127

---

### Post by doorknob60 on 2009-10-25
Install the cx-freeze package. If it's not in your repos (don't think it is), see if the Karmic one works: [http://packages.ubuntu.com/karmic/cx-freeze](http://packages.ubuntu.com/karmic/cx-freeze)

---

### Post by glenuk on 2009-10-25
i've got a .tar.gz file for cxfreeze and trying to install it using the read me instructions which are:

To build:

python setup.py build
python setup.py install

and on doing the first bit i get:

adding base module named StringIO
adding base module named UserDict
adding base module named __future__
adding base module named _abcoll
adding base module named _strptime
adding base module named _threading_local
adding base module named abc
adding base module named base64
adding base module named bdb
adding base module named bisect
adding base module named calendar
adding base module named cmd
adding base module named codecs
adding base module named collections
adding base module named copy
adding base module named copy_reg
adding base module named difflib
adding base module named dis
adding base module named doctest
adding base module named dummy_thread
adding base module named encodings
adding base module named encodings.aliases
adding base module named encodings.ascii
adding base module named encodings.base64_codec
adding base module named encodings.big5
adding base module named encodings.big5hkscs
adding base module named encodings.bz2_codec
adding base module named encodings.charmap
adding base module named encodings.cp037
adding base module named encodings.cp1006
adding base module named encodings.cp1026
adding base module named encodings.cp1140
adding base module named encodings.cp1250
adding base module named encodings.cp1251
adding base module named encodings.cp1252
adding base module named encodings.cp1253
adding base module named encodings.cp1254
adding base module named encodings.cp1255
adding base module named encodings.cp1256
adding base module named encodings.cp1257
adding base module named encodings.cp1258
adding base module named encodings.cp424
adding base module named encodings.cp437
adding base module named encodings.cp500
adding base module named encodings.cp737
adding base module named encodings.cp775
adding base module named encodings.cp850
adding base module named encodings.cp852
adding base module named encodings.cp855
adding base module named encodings.cp856
adding base module named encodings.cp857
adding base module named encodings.cp860
adding base module named encodings.cp861
adding base module named encodings.cp862
adding base module named encodings.cp863
adding base module named encodings.cp864
adding base module named encodings.cp865
adding base module named encodings.cp866
adding base module named encodings.cp869
adding base module named encodings.cp874
adding base module named encodings.cp875
adding base module named encodings.cp932
adding base module named encodings.cp949
adding base module named encodings.cp950
adding base module named encodings.euc_jis_2004
adding base module named encodings.euc_jisx0213
adding base module named encodings.euc_jp
adding base module named encodings.euc_kr
adding base module named encodings.gb18030
adding base module named encodings.gb2312
adding base module named encodings.gbk
adding base module named encodings.hex_codec
adding base module named encodings.hp_roman8
adding base module named encodings.hz
adding base module named encodings.idna
adding base module named encodings.iso2022_jp
adding base module named encodings.iso2022_jp_1
adding base module named encodings.iso2022_jp_2
adding base module named encodings.iso2022_jp_2004
adding base module named encodings.iso2022_jp_3
adding base module named encodings.iso2022_jp_ext
adding base module named encodings.iso2022_kr
adding base module named encodings.iso8859_1
adding base module named encodings.iso8859_10
adding base module named encodings.iso8859_11
adding base module named encodings.iso8859_13
adding base module named encodings.iso8859_14
adding base module named encodings.iso8859_15
adding base module named encodings.iso8859_16
adding base module named encodings.iso8859_2
adding base module named encodings.iso8859_3
adding base module named encodings.iso8859_4
adding base module named encodings.iso8859_5
adding base module named encodings.iso8859_6
adding base module named encodings.iso8859_7
adding base module named encodings.iso8859_8
adding base module named encodings.iso8859_9
adding base module named encodings.johab
adding base module named encodings.koi8_r
adding base module named encodings.koi8_u
adding base module named encodings.latin_1
adding base module named encodings.mac_arabic
adding base module named encodings.mac_centeuro
adding base module named encodings.mac_croatian
adding base module named encodings.mac_cyrillic
adding base module named encodings.mac_farsi
adding base module named encodings.mac_greek
adding base module named encodings.mac_iceland
adding base module named encodings.mac_latin2
adding base module named encodings.mac_roman
adding base module named encodings.mac_romanian
adding base module named encodings.mac_turkish
adding base module named encodings.mbcs
adding base module named encodings.palmos
adding base module named encodings.ptcp154
adding base module named encodings.punycode
adding base module named encodings.quopri_codec
adding base module named encodings.raw_unicode_escape
adding base module named encodings.rot_13
adding base module named encodings.shift_jis
adding base module named encodings.shift_jis_2004
adding base module named encodings.shift_jisx0213
adding base module named encodings.string_escape
adding base module named encodings.tis_620
adding base module named encodings.undefined
adding base module named encodings.unicode_escape
adding base module named encodings.unicode_internal
adding base module named encodings.utf_16
adding base module named encodings.utf_16_be
adding base module named encodings.utf_16_le
adding base module named encodings.utf_32
adding base module named encodings.utf_32_be
adding base module named encodings.utf_32_le
adding base module named encodings.utf_7
adding base module named encodings.utf_8
adding base module named encodings.utf_8_sig
adding base module named encodings.uu_codec
adding base module named encodings.zlib_codec
adding base module named functools
adding base module named genericpath
adding base module named getopt
adding base module named gettext
adding base module named heapq
adding base module named inspect
adding base module named keyword
adding base module named linecache
adding base module named locale
adding base module named opcode
adding base module named optparse
adding base module named os
adding base module named pdb
adding base module named pickle
adding base module named posixpath
adding base module named pprint
adding base module named quopri
adding base module named random
adding base module named re
adding base module named repr
adding base module named shlex
adding base module named sre_compile
adding base module named sre_constants
adding base module named sre_parse
adding base module named stat
adding base module named string
adding base module named stringprep
adding base module named struct
adding base module named subprocess
adding base module named tempfile
adding base module named textwrap
adding base module named threading
adding base module named token
adding base module named tokenize
adding base module named traceback
adding base module named types
adding base module named unittest
adding base module named warnings
running build
running build_py
creating build/lib.linux-i686-2.6
creating build/lib.linux-i686-2.6/cx_Freeze
copying cx_Freeze/finder.py -> build/lib.linux-i686-2.6/cx_Freeze
copying cx_Freeze/freezer.py -> build/lib.linux-i686-2.6/cx_Freeze
copying cx_Freeze/dist.py -> build/lib.linux-i686-2.6/cx_Freeze
copying cx_Freeze/main.py -> build/lib.linux-i686-2.6/cx_Freeze
copying cx_Freeze/windist.py -> build/lib.linux-i686-2.6/cx_Freeze
copying cx_Freeze/hooks.py -> build/lib.linux-i686-2.6/cx_Freeze
copying cx_Freeze/__init__.py -> build/lib.linux-i686-2.6/cx_Freeze
running build_ext
building 'cx_Freeze.util' extension
creating build/temp.linux-i686-2.6/source
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -I/usr/include/python2.6 -c source/util.c -o build/temp.linux-i686-2.6/source/util.o
source/util.c:6:20: error: Python.h: No such file or directory
source/util.c:405: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
source/util.c:419: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_ModuleMethods’
source/util.c:456: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
source/util.c: In function ‘initutil’:
source/util.c:490: warning: implicit declaration of function ‘Module_Initialize’
error: command 'gcc' failed with exit status 1

---

### Post by doorknob60 on 2009-10-25
Hmm, I've never tried manually compiling cxfreeze so I can't really help you there, but I suggest in the fofix folder, open the src directory, and run python FoFiX.py See if the game runs well like that. If so, there's no need to compile.

---

### Post by glenuk on 2009-10-25
is there an easier way of installing it as i only get the src option for downloading from the website you gave
thanks 
glen

---

### Post by DoktorSeven on 2009-10-25
All you have to do is make sure you have all the dependencies listed on their website:
[http://code.google.com/p/fofix/wiki/RunningUnderGNULinux#Install_dependencies](http://code.google.com/p/fofix/wiki/RunningUnderGNULinux#Install_dependencies)
then download and extract the "source" archive.  No compilation necessary though, since if you have all the dependencies listed, all you have to do is change to the src directory where you extracted it (**cd ~/fofix-3.120/src** if you extraced to your home directory) and type
**python FoFiX.py**

You can create a launcher by creating a text file like this:
[b]#!/bin/bash
cd ~/fofix-3.20/src
python FoFiX.py[/b]

(of course, change the path if you extracted it elsewhere).  Make it executable (chmod +x fofixlaunch or whatever you called it or open the properties in your file browser) and you can run it like anything else.

---

### Post by glenuk on 2009-10-25
i've made a launcher by right clicking the desktop & using the coding you mentioned but it comes up with:
"there was an error launching the application, Details: Failed to execute child process "cd" (No such file or directory)"
thanks
glen

---

### Post by DoktorSeven on 2009-10-25
> **glenuk said:**
> i've made a launcher by right clicking the desktop & using the coding you mentioned but it comes up with:
"there was an error launching the application, Details: Failed to execute child process "cd" (No such file or directory)"
thanks
glen

Did you put
**#!/bin/bash**
at the beginning of the text file?

---

### Post by glenuk on 2009-10-25
at first i was stupid & just put the code in the bit where it said command but then i made a new file in the src folder then browsed to that file where it said command and now when i try & click on that it says:
"Details: Failed to execute child process "/home/penguin/fofix-3.120/src/launcher" (Permission denied)"
thanks 
glen

---

### Post by DoktorSeven on 2009-10-25
As I said, you're going to have to activate the execute flag in the permissions of that file.  I'm not sure what file browser you use but it should be somewhere in the properties of that file, or you can do it by commandline with **chmod +x launcher** when you're in the fofix-3.120/src directory.

---

### Post by glenuk on 2009-10-25
i've checked the box that says allow executing file as program but it doesn't do anything
glen

---

### Post by DoktorSeven on 2009-10-25
Hm.  Should work.  Try the commandline method.  Find your shell program (Gnome: gnome-terminal; KDE: konsole; not sure if you run some other desktop, just look for something called "terminal" or similar).

**cd ~/fofix-3.120/src**
**chmod +x launcher**
**./launcher**

---

### Post by glenuk on 2009-10-25
i'm using gnome & have no other os on my system

i put 'chmod +x launcher' into the terminal & all that happend was that it just went down to 'penguin@penguin-desktop:~/fofix-3.120/src$' again so i put './launcher' in & the game launched
glen

---

### Post by glenuk on 2009-10-25
if its of any help i've just noticed that when i right click on the file i created in the src file & click the open with tab the wine windows program loader is selected could this be the problem?
glen

---

### Post by DoktorSeven on 2009-10-26
Not sure why it would do that, as long as you don't have any filename extension (like .exe or whatever) to your launcher and it's marked executable it should just launch normally.

---

### Post by alienduce on 2010-01-04
ariel@skynet:/usr/local/fofix-3.121$ make dist
/bin/sh: svn: not found
--- Detected version: 3.121~
--- Building binary
cxfreeze --target-dir dist \
--exclude-modules tcl,tk,Tkinter \
--include-modules \
encodings.string_escape,\
encodings.iso8859_1,\
SongChoosingScene,\
GuitarScene,\
ctypes.util,pkg_resources,weakref,Image,\
OpenGL,OpenGL.platform.glx,OpenGL.arrays.ctypesarrays,OpenGL.arrays.numpymodule,OpenGL.arrays.lists,OpenGL.arrays.numbers,OpenGL.arrays.strings,\
xml.sax.drivers2.drv_pyexpat,\
GameResultsScene src/FoFiX.py
Traceback (most recent call last):
  File "/usr/bin/cxfreeze", line 5, in <module>
    main()
  File "/usr/lib/pymodules/python2.6/cx_Freeze/main.py", line 170, in main
    freezer.Freeze()
  File "/usr/lib/pymodules/python2.6/cx_Freeze/freezer.py", line 405, in Freeze
    self._FreezeExecutable(executable)
  File "/usr/lib/pymodules/python2.6/cx_Freeze/freezer.py", line 145, in _FreezeExecutable
    finder = self._GetModuleFinder(exe)
  File "/usr/lib/pymodules/python2.6/cx_Freeze/freezer.py", line 251, in _GetModuleFinder
    finder.IncludeModule(name)
  File "/usr/lib/pymodules/python2.6/cx_Freeze/finder.py", line 397, in IncludeModule
    module = self._ImportModule(name, deferredImports)
  File "/usr/lib/pymodules/python2.6/cx_Freeze/finder.py", line 160, in _ImportModule
    deferredImports)
  File "/usr/lib/pymodules/python2.6/cx_Freeze/finder.py", line 246, in _InternalImportModule
    parentModule)
  File "/usr/lib/pymodules/python2.6/cx_Freeze/finder.py", line 281, in _LoadModule
    self._ScanCode(module.code, module, deferredImports)
  File "/usr/lib/pymodules/python2.6/cx_Freeze/finder.py", line 348, in _ScanCode
    module, relativeImportIndex)
  File "/usr/lib/pymodules/python2.6/cx_Freeze/finder.py", line 176, in _ImportModule
    deferredImports)
  File "/usr/lib/pymodules/python2.6/cx_Freeze/finder.py", line 246, in _InternalImportModule
    parentModule)
  File "/usr/lib/pymodules/python2.6/cx_Freeze/finder.py", line 281, in _LoadModule
    self._ScanCode(module.code, module, deferredImports)
  File "/usr/lib/pymodules/python2.6/cx_Freeze/finder.py", line 348, in _ScanCode
    module, relativeImportIndex)
  File "/usr/lib/pymodules/python2.6/cx_Freeze/finder.py", line 176, in _ImportModule
    deferredImports)
  File "/usr/lib/pymodules/python2.6/cx_Freeze/finder.py", line 246, in _InternalImportModule
    parentModule)
  File "/usr/lib/pymodules/python2.6/cx_Freeze/finder.py", line 281, in _LoadModule
    self._ScanCode(module.code, module, deferredImports)
  File "/usr/lib/pymodules/python2.6/cx_Freeze/finder.py", line 348, in _ScanCode
    module, relativeImportIndex)
  File "/usr/lib/pymodules/python2.6/cx_Freeze/finder.py", line 176, in _ImportModule
    deferredImports)
  File "/usr/lib/pymodules/python2.6/cx_Freeze/finder.py", line 246, in _InternalImportModule
    parentModule)
  File "/usr/lib/pymodules/python2.6/cx_Freeze/finder.py", line 281, in _LoadModule
    self._ScanCode(module.code, module, deferredImports)
  File "/usr/lib/pymodules/python2.6/cx_Freeze/finder.py", line 348, in _ScanCode
    module, relativeImportIndex)
  File "/usr/lib/pymodules/python2.6/cx_Freeze/finder.py", line 176, in _ImportModule
    deferredImports)
  File "/usr/lib/pymodules/python2.6/cx_Freeze/finder.py", line 246, in _InternalImportModule
    parentModule)
  File "/usr/lib/pymodules/python2.6/cx_Freeze/finder.py", line 259, in _LoadModule
    module.code = compile(fp.read() + "\n", path, "exec")
  File "src/Audio.py", line 7
    msgid ""
           ^
SyntaxError: invalid syntax
make: *** [dist] Error 1

I don't know how to solve that.

---

