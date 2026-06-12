---
title: "error while loading shared libraries: libfftw3f.so.3"
date: 2010-04-27
forum: Education &amp; Science
---

### Post by joyssstan on 2010-04-27
Hi.

I installed fftw-3.2.2 and gromacs-4.0.4 on Ubuntu-9.0.4 with the below command:

./configure --enable-float --enable--sse --enable-threads --enable-shared
make
make install 

./configure --enable-shared
make
make install
make links

Everything seem to be working fine. Then I typed 'luck' to test whether I can access GROMACS or not, below error occurs:

luck: error while loading shared libraries: libfftw3f.so.3: cannot open shared object file: No such file or directory

Can anyone help me to solve this?

Thanks in advance.:)

---

### Post by Azrael3000 on 2010-04-27
as far as I can remember I always linked the fftw library directly to my own files.

maybe you can tell me what the output of
```

whereis libfftw3f

```
is. If you can't find it in /usr/lib maybe try linking from wherever it is now to /usr/lib/libfftw3f.so.3

---

