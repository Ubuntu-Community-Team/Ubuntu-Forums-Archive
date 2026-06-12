---
title: "Compiling dxflib"
date: 2009-01-15
forum: General Help
---

### Post by mrrain7 on 2009-01-15
I'm trying to compile dxflib so I can use vec2web.
I run configure and everything goes fine, but when I type make this is what I get:
```
g++ -I./src -g -O2  -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DLINUX=1 -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIMITS_H=1 -c src/dl_writer_ascii.cpp -o src/dl_writer_ascii.o
In file included from src/dl_writer_ascii.h:35,
                 from src/dl_writer_ascii.cpp:34:
src/dl_writer.h: In member function ‘void DL_Writer::entityAttributes(const DL_Attributes&) const’:
src/dl_writer.h:341: error: ‘strcasecmp’ no se declaró en este ámbito
src/dl_writer_ascii.cpp: In member function ‘virtual void DL_WriterA::dxfReal(int, double) const’:
src/dl_writer_ascii.cpp:72: error: ‘strlen’ no se declaró en este ámbito
src/dl_writer_ascii.cpp:81: error: ‘strlen’ no se declaró en este ámbito
src/dl_writer_ascii.cpp: In static member function ‘static void DL_WriterA::strReplace(char*, char, char)’:
src/dl_writer_ascii.cpp:147: error: ‘strlen’ no se declaró en este ámbito
make: *** [src/dl_writer_ascii.o] Error 1

```


Any ideas?

---

### Post by jagipson on 2009-03-16
Similar problem here:

```
$ export QTDIR=/usr/lib/qt3/
$ make
test -d ./include || mkdir -p ./include
( cd ./include; rm -f *.h; \
	for hf in `find ../src -name '*.h'`; do \
		if [ "x$OS" = "xWindows_NT" ]; then \
			cp "$hf" .; \
		else \
			ln -s "$hf" 2> /dev/null; \
		fi \
	done )
gcc -I./src -g -O2  -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DLINUX=1 -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIMITS_H=1  -c src/dl_writer_ascii.cpp -o src/dl_writer_ascii.o
In file included from src/dl_writer_ascii.h:35,
                 from src/dl_writer_ascii.cpp:34:
src/dl_writer.h: In member function ‘void DL_Writer::entityAttributes(const DL_Attributes&) const’:
src/dl_writer.h:333: error: ‘strcasecmp’ was not declared in this scope
src/dl_writer_ascii.cpp: In member function ‘virtual void DL_WriterA::dxfReal(int, double) const’:
src/dl_writer_ascii.cpp:72: error: ‘strlen’ was not declared in this scope
src/dl_writer_ascii.cpp:81: error: ‘strlen’ was not declared in this scope
src/dl_writer_ascii.cpp: In static member function ‘static void DL_WriterA::strReplace(char*, char, char)’:
src/dl_writer_ascii.cpp:147: error: ‘strlen’ was not declared in this scope
make: *** [src/dl_writer_ascii.o] Error 1

```

---

### Post by Tomtefar on 2009-06-18
Have a look at the official forum:
[http://www.ribbonsoft.com/forum/viewtopic.php?t=803](http://www.ribbonsoft.com/forum/viewtopic.php?t=803)
What you need to do is install gcc-4.2 and compile it with that instead of the default 4.3

---

### Post by jestin on 2010-10-01
The forum has moved to [http://www.ribbonsoft.com/rsforum/viewtopic.php?t=803](http://www.ribbonsoft.com/rsforum/viewtopic.php?t=803)

---

