---
title: "Dwarf Fortress complains included file doesn't exists"
date: 2012-05-16
forum: Gaming &amp; Leisure
---

### Post by dbbolton on 2012-05-16
I'm trying to set up Dwarf Fortress 34_08 on oneiric. After extracting the tarball, this is what happens:

```

&#9795; ~/Downloads/df_linux » ls
command line.txt  df                g_src  raw           readme.txt         sdl
data              file changes.txt  libs   README.linux  release notes.txt

&#9795; ~/Downloads/df_linux » ls -l df
-rwxr--r-- 1 dbb dbb 243 2012-05-14 05:43 df

&#9795; ~/Downloads/df_linux » ./df
./df: 6: ./libs/Dwarf_Fortress: not found

&#9795; ~/Downloads/df_linux » ls libs
Dwarf_Fortress  libgcc_s.so.1  libgraphics.so  libstdc++.so.6

&#9795; ~/Downloads/df_linux » file ./libs/Dwarf_Fortress
./libs/Dwarf_Fortress: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.8, stripped

```I've read conflicting information on how to run this 32-bit binary, so I'm not sure how to proceed. Older docs say to install ia32-libs, which aptitude says is impossible. A forum post says to prepend then env variable LD_LIBRARY_PATH=/usr/lib32 before the binary, but that did nothing. It certainly doesn't explain why an existing file is said not to exist.

---

### Post by Flamer Shaftglutton on 2012-05-18
I have had this problem as well. The file(s) aren't actually missing. DF is supposed to tell you that libraries are missing, yet doesn't. You will need these 32-bit compatibility libraries: [click me](http://www.archlinux.org/packages/multilib/x86_64/dwarffortress/). 

However, those are the Arch libraries, not the Ubuntu libraries. You'll have to find the Ubuntu equivalents and apt-get those. Just make sure '32' or 'i386' is in the library name somewhere.

---

