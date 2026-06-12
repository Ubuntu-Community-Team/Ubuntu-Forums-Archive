---
title: "libemf deb package somewhere?"
date: 2006-08-10
forum: Desktop Environments
---

### Post by RikoW on 2006-08-10
hi,

i'm looking for the ubuntu deb package for libemf (enhanced meta file lib). 

It's not in the repositories and I didn't manage to compile it from source, even though i believe I have all the necessary packages installed. Errors I get after ./configure and make:

```
> make
Making all in include
make[1]: Entering directory `/home/wichmann/Desktop/libEMF-1.0/include'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/wichmann/Desktop/libEMF-1.0/include'
Making all in libemf
make[1]: Entering directory `/home/wichmann/Desktop/libEMF-1.0/libemf'
source='libemf.cpp' object='libemf.lo' libtool=yes \
        depfile='.deps/libemf.Plo' tmpdepfile='.deps/libemf.TPlo' \
        depmode=gcc3 /bin/sh ../config/depcomp \
        /bin/sh ../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../config -I../include    -g -O2 -D_REENTRANT -DPTHREADS -c -o libemf.lo `test -f libemf.cpp || echo './'`libemf.cpp
mkdir .libs
g++ -DHAVE_CONFIG_H -I. -I. -I../config -I../include -g -O2 -D_REENTRANT -DPTHREADS -c libemf.cpp -MT libemf.lo -MD -MP -MF .deps/libemf.TPlo  -fPIC -DPIC -o .libs/libemf.lo
libemf.cpp: In static member function 'static bool EMF::DATASTREAM::bigEndian()':libemf.cpp:51: error: 'cerr' was not declared in this scope
libemf.cpp:51: error: 'endl' was not declared in this scope
libemf.cpp: In function 'HENHMETAFILE CloseEnhMetaFile(HDC)':
libemf.cpp:852: error: 'mem_fun1' is not a member of 'std'
libemf.cpp: In function 'HENHMETAFILE CloseEnhMetaFileWithFILE(HDC)':
libemf.cpp:899: error: 'mem_fun1' is not a member of 'std'
libemf.cpp: In function 'HENHMETAFILE GetEnhMetaFileW(const WCHAR*)':
libemf.cpp:1035: error: 'cerr' was not declared in this scope
libemf.cpp:1035: error: 'endl' was not declared in this scope
libemf.cpp:1053: error: 'cerr' was not declared in this scope
libemf.cpp:1054: error: 'endl' was not declared in this scope
make[1]: *** [libemf.lo] Error 1
make[1]: Leaving directory `/home/wichmann/Desktop/libEMF-1.0/libemf'
make: *** [all-recursive] Error 1

```

I found an rpm package, which I , trying my luck, converted to deb via alien and installed. But that wasn't successful either :(

Anybody knows of a secret repository where I might find it (or how to fix the compiling problem above - seems like some standard functions cannot be found ... weired.

Thanks,
            Riko

---

### Post by moma on 2006-08-10
The code seems to be rather old. It even uses windows calls and linkage to wine.

Take these actions.

1) Modify libemf/libemf.h file 
$ [COLOR="Green"]gedit libemf/libemf.h[/COLOR]

and add these line to the header section.
```
#include <iostream>
#include <function.h>   
```

2) Edit libemf/libemf.cpp
$ [COLOR="Green"]gedit libemf/libemf.cpp[/COLOR]

Add this line after "#include "libemf.h"

```
using namespace std;
```

and remove **std::** before all mem_fun1(....) function calls.

A sample:
```
  std::for_each( dc->records.begin(), dc->records.end(),
                     std::bind2nd( mem_fun1( &EMF::METARECORD::serialize ),
                                   dc->ds ) );
```

2)  Try to configure with gcc-4.x
$ [COLOR="Green"]./configure [/COLOR]

If it fails then install gcc-3.4 package and  configure for  gcc-3.4 compiler suite.
$ [COLOR="Green"]CC=gcc-3.4 CXX=g++-3.4 ./configure[/COLOR]

No guarantees thou !
Have fun.

---

### Post by RikoW on 2006-08-10
Edit: ahh, while I was writing this I saw the post of moma! Thanks :)
      The full fix is below.

Why do I need it? emf is a nice scalable format which can be easily import into OOo. With pstoedit I can convert pdf, (e)ps pictures created by various plotting applications ) to emf and use it with OOo. Avoids the fuzziness of gifs or jpegs when you need to scale them.

Ok, and here is now the post I started when moma replied :)

-------------

ok, solved the compiling problem. Sounded like the programmers were kind of sloppy in inlcudign standard routines which was forgiven by older versions of gcc, which now is much stricter. I had to patch the files libemf/libemf.cpp and libemf/libemf.h:

```
> diff -p libemf.h libemf.h.save
*** libemf.h    2006-08-10 10:34:33.000000000 +0200
--- libemf.h.save       2006-08-10 10:33:20.000000000 +0200
***************
*** 21,33 ****
  #ifndef _LIBEMF_H
  #define _LIBEMF_H 1

- #include <iostream>
- #include <ostream>
  #include <cmath>
  #include <vector>
  #include <map>
  #include <functional>
- #include <ext/functional>
  #include <algorithm>

  #include <config.h>
--- 21,30 ----

```


```
> diff -p libemf.cpp libemf.cpp.save
*** libemf.cpp  2006-08-10 10:39:04.000000000 +0200
--- libemf.cpp.save     2006-08-10 10:35:42.000000000 +0200
*************** namespace EMF {
*** 48,54 ****
        be32 = !be16;

      if ( be32 != be16 ) {
!       std::cerr << "endian-ness not consistent between short's and int's!" << std::endl;
        ::abort();
      }

--- 48,54 ----
        be32 = !be16;

      if ( be32 != be16 ) {
!       cerr << "endian-ness not consistent between short's and int's!" << endl;        ::abort();
      }

*************** extern "C" {
*** 849,855 ****
      if ( dc->fp ) {

        std::for_each( dc->records.begin(), dc->records.end(),
!                    std::bind2nd( __gnu_cxx::mem_fun1( &EMF::METARECORD::serialize ),
                                   dc->ds ) );
        fclose( dc->fp );

--- 849,855 ----
      if ( dc->fp ) {

        std::for_each( dc->records.begin(), dc->records.end(),
!                    std::bind2nd( std::mem_fun1( &EMF::METARECORD::serialize ),                                   dc->ds ) );
        fclose( dc->fp );

*************** extern "C" {
*** 896,902 ****
      if ( dc->fp ) {

        std::for_each( dc->records.begin(), dc->records.end(),
!                    std::bind2nd( __gnu_cxx::mem_fun1( &EMF::METARECORD::serialize ),
                                   dc->ds ) );
      }

--- 896,902 ----
      if ( dc->fp ) {

        std::for_each( dc->records.begin(), dc->records.end(),
!                    std::bind2nd( std::mem_fun1( &EMF::METARECORD::serialize ),                                   dc->ds ) );
      }

*************** extern "C" {
*** 1032,1038 ****
        if ( feof( fp ) ) break;

        if ( emr.nSize == 0 ) {
!       std::cerr << "GetEnhMetaFileW error: record size == 0. cannot continue" << std::endl;
        fclose( fp );
        return 0;
        }
--- 1032,1038 ----
        if ( feof( fp ) ) break;

        if ( emr.nSize == 0 ) {
!       cerr << "GetEnhMetaFileW error: record size == 0. cannot continue" << endl;
        fclose( fp );
        return 0;
        }
*************** extern "C" {
*** 1050,1057 ****
        dc->appendRecord( record );
        }
        else
!       std::cerr << "GetEnhMetaFileW warning: read unknown record type " << emr.iType
!            << " of size " << emr.nSize << std::endl;

        // Regardless, position ourselves at the next record.
        fseek( fp, next_position, SEEK_SET );
--- 1050,1057 ----
        dc->appendRecord( record );
        }
        else
!       cerr << "GetEnhMetaFileW warning: read unknown record type " << emr.iType
!            << " of size " << emr.nSize << endl;

        // Regardless, position ourselves at the next record.
        fseek( fp, next_position, SEEK_SET );

```

Found a hint for that on the libemf developers mailing list.

Cheers,

           Riko

---

### Post by moma on 2006-08-10
Yep.

---

