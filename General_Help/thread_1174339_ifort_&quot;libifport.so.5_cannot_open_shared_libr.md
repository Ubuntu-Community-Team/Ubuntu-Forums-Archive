---
title: "ifort &quot;libifport.so.5 cannot open shared library&quot; error"
date: 2009-05-30
forum: General Help
---

### Post by Lyuokdea on 2009-05-30
I have installed the ifort and icc compilers and am trying to run an academic program. The program compiles fine, however, when i try to run it, i instantaneously get an error:

"libifport.so.5 cannot open shared library"

I've found the file, it was installed to /opt/intel/Compiler/11.0/083/lib/intel64/ (with another 32 bit version installed, but i'm trying to run with the 64 bit compilers.) I already have this directory in my path (to get ifort itself to run). 

I read that you can set LD_LIBRARY_PATH = /opt/intel/Compiler/11.0/083/lib/intel64/ , though that is not a great option. However, I tried that, and it didn't work. Is there anyway to solve this by adding the path directly into the make file, or into flags for the ifort compilation?

Thanks,

~Lyuokdea

---

