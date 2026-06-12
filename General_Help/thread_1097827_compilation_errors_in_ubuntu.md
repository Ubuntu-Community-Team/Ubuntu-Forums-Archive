---
title: "compilation errors in ubuntu"
date: 2009-03-16
forum: General Help
---

### Post by bgokaraju on 2009-03-16
Hey I am having following compilation errors while installing a software.

I appreciate any help in this.

-lc -L/usr/lib/gcc/i486-linux-gnu/4.1.3 -lgcc_eh 

/seadas5.3//src/lib3/hdf4/lib/libmfhdf.a(error.o): In function `nc_serror':

error.c:(.text+0x73): warning: `sys_errlist' is deprecated; use `strerror' or `strerror_r' instead

error.c:(.text+0x6a): warning: `sys_nerr' is deprecated; use `strerror' or `strerror_r' instead

ld: cannot find -lgcc_eh


Thanks:
bgokaraju

---

### Post by LegendofTom on 2009-03-16
What program is this?  It looks like either the program is faulty or gcc is missing something.

---

### Post by bgokaraju on 2009-03-16
Hey this is a NASA seadas open source software i'm trying to recompile in ubuntu 8.10. The program is not faulty and I hope its missing some gcc libraries. but, i dont know how to fix this. Please guide me if you can in this.

Thanks,
bgokaraju



> **LegendofTom said:**
> What program is this?  It looks like either the program is faulty or gcc is missing something.

---

