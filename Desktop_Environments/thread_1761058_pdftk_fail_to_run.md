---
title: "pdftk fail to run"
date: 2011-05-17
forum: Desktop Environments
---

### Post by tanyeun on 2011-05-17
recently I found that I couldn't run pdftk anymore
whenever I type $pdftk it shows:
> 
libgcj failure: gcj linkage error.
Incorrect library ABI version detected.  Aborting.

Aborted


I guess it might because I build gcc-4.5.2 from source 
and somehow mess up with the gcj linker but I have no
clue how to fix it.

I even try to build it from source
I followed the instruction here: [http://www.pdflabs.com/docs/build-pdftk/](http://www.pdflabs.com/docs/build-pdftk/)
when I run $ apropos gcc it shows:
> 
c89-gcc (1)          - ANSI (1989) C compiler
c99-gcc (1)          - ANSI (1999) C compiler
gcc (1)              - GNU project C and C++ compiler
gcc-4.1 (1)          - GNU project C and C++ compiler
gcc-4.2 (1)          - GNU project C and C++ compiler
gcc-4.4 (1)          - GNU project C and C++ compiler
gcc-4.6 (1)          - GNU project C and C++ compiler
gccbug-4.1 (1)       - Reporting GCC Bugs
i486-linux-gnu-gcc (1) - GNU project C and C++ compiler
i486-linux-gnu-gcc-4.1 (1) - GNU project C and C++ compiler
i486-linux-gnu-gcc-4.2 (1) - GNU project C and C++ compiler
i486-linux-gnu-gcc-4.4 (1) - GNU project C and C++ compiler
i486-linux-gnu-gcc-4.6 (1) - GNU project C and C++ compiler
winegcc (1)          - Wine C and C++ MinGW Compatible Compiler

when I run $ apropos gcj it shows:
> 
gcj-dbtool (1)       - Manipulate class file mapping databases for libgcj
gcj-dbtool-4.3 (1)   - Manipulate class file mapping databases for libgcj
gcj-dbtool-4.4 (1)   - Manipulate class file mapping databases for libgcj
gcj (1)              - Ahead-of-time compiler for the Java language
gcjh (1)             - - generate header files from Java class files
rebuild-gcj-db (1)   - Merge the per-solib databases made by aot-compile into...

I have no clue which version of gcc I should use
I tried gcc-4.4 gcc-4.6 both shown gcj-4.4/4.6 not found
and gcc-4.5.2 generates lots of ugly error message

any ideas?

thx a lot

---

