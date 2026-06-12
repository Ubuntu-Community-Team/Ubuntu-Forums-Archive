---
title: "GTKRadiant Issues"
date: 2010-09-07
forum: Gaming &amp; Leisure
---

### Post by feardotcom on 2010-09-07
Trying to compile GTKRadiant and i get these issues executing scons...anyone here that can help?

```
scons: Reading SConscript files ...
SCons.Script:4: DeprecationWarning: The popen2 module is deprecated.  Use the subprocess module.
SCons 1.2.0.d20100117
OS="Linux"
version: 1.5.0
minor: 0 major: 5
about message is in /home/chris/GtkRadiant/include/aboutmsg.default
about: Custom build based on trunk\ngcc version: 4.4.3

scons: warning: The env.Copy() method is deprecated; use the env.Clone() method instead.
File "/home/chris/GtkRadiant/SConscript", line 19, in <module>

scons: warning: Two different environments were specified for target tools/quake3/common/cmdlib.o,
	but they appear to have the same action: $CC -o $TARGET -c $CFLAGS $CCFLAGS $_CCCOMCOM $SOURCES
File "/home/chris/GtkRadiant/SConscript", line 200, in <module>

scons: warning: Two different environments were specified for target tools/quake3/common/imagelib.o,
	but they appear to have the same action: $CC -o $TARGET -c $CFLAGS $CCFLAGS $_CCCOMCOM $SOURCES
File "/home/chris/GtkRadiant/SConscript", line 200, in <module>

scons: warning: Two different environments were specified for target tools/quake3/common/inout.o,
	but they appear to have the same action: $CC -o $TARGET -c $CFLAGS $CCFLAGS $_CCCOMCOM $SOURCES
File "/home/chris/GtkRadiant/SConscript", line 200, in <module>

scons: warning: Two different environments were specified for target tools/quake3/common/scriplib.o,
	but they appear to have the same action: $CC -o $TARGET -c $CFLAGS $CCFLAGS $_CCCOMCOM $SOURCES
File "/home/chris/GtkRadiant/SConscript", line 200, in <module>

scons: warning: Two different environments were specified for target tools/quake3/common/unzip.o,
	but they appear to have the same action: $CC -o $TARGET -c $CFLAGS $CCFLAGS $_CCCOMCOM $SOURCES
File "/home/chris/GtkRadiant/SConscript", line 200, in <module>

scons: warning: Two different environments were specified for target tools/quake3/common/vfs.o,
	but they appear to have the same action: $CC -o $TARGET -c $CFLAGS $CCFLAGS $_CCCOMCOM $SOURCES
File "/home/chris/GtkRadiant/SConscript", line 200, in <module>

scons: warning: Two different environments were specified for target tools/quake2/common/bspfile.o,
	but they appear to have the same action: $CC -o $TARGET -c $CFLAGS $CCFLAGS $_CCCOMCOM $SOURCES
File "/home/chris/GtkRadiant/SConscript", line 290, in <module>

scons: warning: Two different environments were specified for target tools/quake2/common/cmdlib.o,
	but they appear to have the same action: $CC -o $TARGET -c $CFLAGS $CCFLAGS $_CCCOMCOM $SOURCES
File "/home/chris/GtkRadiant/SConscript", line 290, in <module>

scons: warning: Two different environments were specified for target tools/quake2/common/inout.o,
	but they appear to have the same action: $CC -o $TARGET -c $CFLAGS $CCFLAGS $_CCCOMCOM $SOURCES
File "/home/chris/GtkRadiant/SConscript", line 290, in <module>

scons: warning: Two different environments were specified for target tools/quake2/common/l3dslib.o,
	but they appear to have the same action: $CC -o $TARGET -c $CFLAGS $CCFLAGS $_CCCOMCOM $SOURCES
File "/home/chris/GtkRadiant/SConscript", line 290, in <module>

scons: warning: Two different environments were specified for target tools/quake2/common/lbmlib.o,
	but they appear to have the same action: $CC -o $TARGET -c $CFLAGS $CCFLAGS $_CCCOMCOM $SOURCES
File "/home/chris/GtkRadiant/SConscript", line 290, in <module>

scons: warning: Two different environments were specified for target tools/quake2/common/mathlib.o,
	but they appear to have the same action: $CC -o $TARGET -c $CFLAGS $CCFLAGS $_CCCOMCOM $SOURCES
File "/home/chris/GtkRadiant/SConscript", line 290, in <module>

scons: warning: Two different environments were specified for target tools/quake2/common/md4.o,
	but they appear to have the same action: $CC -o $TARGET -c $CFLAGS $CCFLAGS $_CCCOMCOM $SOURCES
File "/home/chris/GtkRadiant/SConscript", line 290, in <module>

scons: warning: Two different environments were specified for target tools/quake2/common/path_init.o,
	but they appear to have the same action: $CC -o $TARGET -c $CFLAGS $CCFLAGS $_CCCOMCOM $SOURCES
File "/home/chris/GtkRadiant/SConscript", line 290, in <module>

scons: warning: Two different environments were specified for target tools/quake2/common/polylib.o,
	but they appear to have the same action: $CC -o $TARGET -c $CFLAGS $CCFLAGS $_CCCOMCOM $SOURCES
File "/home/chris/GtkRadiant/SConscript", line 290, in <module>

scons: warning: Two different environments were specified for target tools/quake2/common/scriplib.o,
	but they appear to have the same action: $CC -o $TARGET -c $CFLAGS $CCFLAGS $_CCCOMCOM $SOURCES
File "/home/chris/GtkRadiant/SConscript", line 290, in <module>

scons: warning: Two different environments were specified for target tools/quake2/common/threads.o,
	but they appear to have the same action: $CC -o $TARGET -c $CFLAGS $CCFLAGS $_CCCOMCOM $SOURCES
File "/home/chris/GtkRadiant/SConscript", line 290, in <module>

scons: warning: Two different environments were specified for target tools/quake2/common/trilib.o,
	but they appear to have the same action: $CC -o $TARGET -c $CFLAGS $CCFLAGS $_CCCOMCOM $SOURCES
File "/home/chris/GtkRadiant/SConscript", line 290, in <module>
scons: done reading SConscript files.
scons: Building targets ...
scons: building associated VariantDir targets: build/debug
g++ -o build/debug/plugins/archivepak/plugin.os -c -pipe -DPOSIX -DXWINDOWS -W -Wall -Wcast-align -Wcast-qual -Wno-unused-parameter -Wno-non-virtual-dtor -Wreorder -g3 -D_DEBUG -fPIC -fno-exceptions -fno-rtti -DPOSIX -DXWINDOWS -W -Wall -Wcast-align -Wcast-qual -Wno-unused-parameter -g3 -D_DEBUG -fPIC -fPIC -Ibuild/debug/libs -Ilibs -Ibuild/debug/include -Iinclude plugins/archivepak/plugin.cpp
g++ -o build/debug/plugins/archivepak/archive.os -c -pipe -DPOSIX -DXWINDOWS -W -Wall -Wcast-align -Wcast-qual -Wno-unused-parameter -Wno-non-virtual-dtor -Wreorder -g3 -D_DEBUG -fPIC -fno-exceptions -fno-rtti -DPOSIX -DXWINDOWS -W -Wall -Wcast-align -Wcast-qual -Wno-unused-parameter -g3 -D_DEBUG -fPIC -fPIC -Ibuild/debug/libs -Ilibs -Ibuild/debug/include -Iinclude plugins/archivepak/archive.cpp
g++ -o build/debug/plugins/archivepak/pak.os -c -pipe -DPOSIX -DXWINDOWS -W -Wall -Wcast-align -Wcast-qual -Wno-unused-parameter -Wno-non-virtual-dtor -Wreorder -g3 -D_DEBUG -fPIC -fno-exceptions -fno-rtti -DPOSIX -DXWINDOWS -W -Wall -Wcast-align -Wcast-qual -Wno-unused-parameter -g3 -D_DEBUG -fPIC -fPIC -Ibuild/debug/libs -Ilibs -Ibuild/debug/include -Iinclude plugins/archivepak/pak.cpp
g++ -o build/debug/libs/cmdlib/cmdlib.o -c -pipe -DPOSIX -DXWINDOWS -W -Wall -Wcast-align -Wcast-qual -Wno-unused-parameter -Wno-non-virtual-dtor -Wreorder -g3 -D_DEBUG -fPIC -fno-exceptions -fno-rtti -DPOSIX -DXWINDOWS -W -Wall -Wcast-align -Wcast-qual -Wno-unused-parameter -g3 -D_DEBUG -fPIC -Ibuild/debug/libs -Ilibs libs/cmdlib/cmdlib.cpp
ar rc build/debug/libs/libcmdlib.a build/debug/libs/cmdlib/cmdlib.o
ranlib build/debug/libs/libcmdlib.a
g++ -o build/debug/archivepak.so -fPIC -Wl,-fini,fini_stub -L. -static-libgcc -ldl -shared build/debug/plugins/archivepak/plugin.os build/debug/plugins/archivepak/archive.os build/debug/plugins/archivepak/pak.os -Lbuild/debug/libs -Llibs -lcmdlib
CheckLDD(["build/debug/archivepak.so"], ["build/debug/plugins/archivepak/plugin.os", "build/debug/plugins/archivepak/archive.os", "build/debug/plugins/archivepak/pak.os"])
g++ -o build/debug/plugins/archivewad/plugin.os -c -pipe -DPOSIX -DXWINDOWS -W -Wall -Wcast-align -Wcast-qual -Wno-unused-parameter -Wno-non-virtual-dtor -Wreorder -g3 -D_DEBUG -fPIC -fno-exceptions -fno-rtti -DPOSIX -DXWINDOWS -W -Wall -Wcast-align -Wcast-qual -Wno-unused-parameter -g3 -D_DEBUG -fPIC -fPIC -Ibuild/debug/libs -Ilibs -Ibuild/debug/include -Iinclude plugins/archivewad/plugin.cpp
g++ -o build/debug/plugins/archivewad/archive.os -c -pipe -DPOSIX -DXWINDOWS -W -Wall -Wcast-align -Wcast-qual -Wno-unused-parameter -Wno-non-virtual-dtor -Wreorder -g3 -D_DEBUG -fPIC -fno-exceptions -fno-rtti -DPOSIX -DXWINDOWS -W -Wall -Wcast-align -Wcast-qual -Wno-unused-parameter -g3 -D_DEBUG -fPIC -fPIC -Ibuild/debug/libs -Ilibs -Ibuild/debug/include -Iinclude plugins/archivewad/archive.cpp
g++ -o build/debug/plugins/archivewad/wad.os -c -pipe -DPOSIX -DXWINDOWS -W -Wall -Wcast-align -Wcast-qual -Wno-unused-parameter -Wno-non-virtual-dtor -Wreorder -g3 -D_DEBUG -fPIC -fno-exceptions -fno-rtti -DPOSIX -DXWINDOWS -W -Wall -Wcast-align -Wcast-qual -Wno-unused-parameter -g3 -D_DEBUG -fPIC -fPIC -Ibuild/debug/libs -Ilibs -Ibuild/debug/include -Iinclude plugins/archivewad/wad.cpp
g++ -o build/debug/archivewad.so -fPIC -Wl,-fini,fini_stub -L. -static-libgcc -ldl -shared build/debug/plugins/archivewad/plugin.os build/debug/plugins/archivewad/archive.os build/debug/plugins/archivewad/wad.os -Lbuild/debug/libs -Llibs -lcmdlib
CheckLDD(["build/debug/archivewad.so"], ["build/debug/plugins/archivewad/plugin.os", "build/debug/plugins/archivewad/archive.os", "build/debug/plugins/archivewad/wad.os"])
g++ -o build/debug/plugins/archivezip/plugin.os -c -pipe -DPOSIX -DXWINDOWS -W -Wall -Wcast-align -Wcast-qual -Wno-unused-parameter -Wno-non-virtual-dtor -Wreorder -g3 -D_DEBUG -fPIC -fno-exceptions -fno-rtti -DPOSIX -DXWINDOWS -W -Wall -Wcast-align -Wcast-qual -Wno-unused-parameter -g3 -D_DEBUG -fPIC -fPIC -Ibuild/debug/libs -Ilibs -Ibuild/debug/include -Iinclude plugins/archivezip/plugin.cpp
g++ -o build/debug/plugins/archivezip/archive.os -c -pipe -DPOSIX -DXWINDOWS -W -Wall -Wcast-align -Wcast-qual -Wno-unused-parameter -Wno-non-virtual-dtor -Wreorder -g3 -D_DEBUG -fPIC -fno-exceptions -fno-rtti -DPOSIX -DXWINDOWS -W -Wall -Wcast-align -Wcast-qual -Wno-unused-parameter -g3 -D_DEBUG -fPIC -fPIC -Ibuild/debug/libs -Ilibs -Ibuild/debug/include -Iinclude plugins/archivezip/archive.cpp
In file included from plugins/archivezip/archive.cpp:33:
plugins/archivezip/zlibstream.h:25:18: error: zlib.h: No such file or directory
In file included from plugins/archivezip/archive.cpp:33:
plugins/archivezip/zlibstream.h:35: error: ‘z_stream’ does not name a type
plugins/archivezip/zlibstream.h: In constructor ‘DeflatedInputStream::DeflatedInputStream(InputStream&)’:
plugins/archivezip/zlibstream.h:43: error: ‘m_zipstream’ was not declared in this scope
plugins/archivezip/zlibstream.h:47: error: ‘MAX_WBITS’ was not declared in this scope
plugins/archivezip/zlibstream.h:47: error: ‘inflateInit2’ was not declared in this scope
plugins/archivezip/zlibstream.h: In destructor ‘DeflatedInputStream::~DeflatedInputStream()’:
plugins/archivezip/zlibstream.h:51: error: ‘m_zipstream’ was not declared in this scope
plugins/archivezip/zlibstream.h:51: error: ‘inflateEnd’ was not declared in this scope
plugins/archivezip/zlibstream.h: In member function ‘virtual size_t DeflatedInputStream::read(unsigned char*, size_t)’:
plugins/archivezip/zlibstream.h:55: error: ‘m_zipstream’ was not declared in this scope
plugins/archivezip/zlibstream.h:56: error: expected type-specifier before ‘uInt’
plugins/archivezip/zlibstream.h:56: error: expected ‘>’ before ‘uInt’
plugins/archivezip/zlibstream.h:56: error: expected ‘(’ before ‘uInt’
plugins/archivezip/zlibstream.h:56: error: ‘uInt’ was not declared in this scope
plugins/archivezip/zlibstream.h:56: error: expected ‘)’ before ‘;’ token
plugins/archivezip/zlibstream.h:62: error: expected type-specifier before ‘uInt’
plugins/archivezip/zlibstream.h:62: error: expected ‘>’ before ‘uInt’
plugins/archivezip/zlibstream.h:62: error: expected ‘(’ before ‘uInt’
plugins/archivezip/zlibstream.h:62: error: expected ‘)’ before ‘;’ token
plugins/archivezip/zlibstream.h:64: error: ‘Z_SYNC_FLUSH’ was not declared in this scope
plugins/archivezip/zlibstream.h:64: error: ‘inflate’ was not declared in this scope
plugins/archivezip/zlibstream.h:64: error: ‘Z_OK’ was not declared in this scope
In file included from plugins/archivezip/archive.cpp:95:
plugins/archivezip/pkzip.h: At global scope:
plugins/archivezip/pkzip.h:75: warning: missing braces around initializer for ‘char [4]’
plugins/archivezip/pkzip.h:114: warning: missing braces around initializer for ‘char [4]’
plugins/archivezip/pkzip.h:141: warning: missing braces around initializer for ‘char [4]’
plugins/archivezip/pkzip.h:188: warning: missing braces around initializer for ‘char [4]’
plugins/archivezip/archive.cpp: In member function ‘bool ZipArchive::read_record()’:
plugins/archivezip/archive.cpp:142: error: ‘Z_DEFLATED’ was not declared in this scope
plugins/archivezip/archive.cpp:182: error: ‘Z_DEFLATED’ was not declared in this scope
scons: *** [build/debug/plugins/archivezip/archive.os] Error 1
scons: building terminated because of errors.
``` 

No idea what scons even does, nor why pkzip is even being used. Any help would be greatly appreciated. Thanks

---

### Post by J.K.Makowka on 2010-09-07
Tried netradiant instead?

[http://dev.alientrap.org/wiki/netradiant](http://dev.alientrap.org/wiki/netradiant)

I think that is less of a mess to complile.

---

### Post by Perfect Storm on 2010-09-07
> plugins/archivezip/zlibstream.h:25:18: error: zlib.h: No such file or directory

Install -dev package of zlib.

---

### Post by feardotcom on 2010-09-07
> **J.K.Makowka said:**
> Tried netradiant instead?

[http://dev.alientrap.org/wiki/netradiant](http://dev.alientrap.org/wiki/netradiant)

I think that is less of a mess to complile.


That looks like its for Q3 mods, not Q4 or D3 (IDTech 4 Engine)

@AI

I think whats happened is because i haven't installed any of the -dev packages of the required packages listed in the compile info file thats what the problem is here. Will find out after synaptic finishes i guess.

---

### Post by J.K.Makowka on 2010-09-08
try DarkRadiant then:
[http://darkradiant.sourceforge.net/](http://darkradiant.sourceforge.net/)

---

### Post by feardotcom on 2010-09-09
Wow, yeah, that looks promising.

---

