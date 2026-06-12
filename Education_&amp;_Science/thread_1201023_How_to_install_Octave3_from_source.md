---
title: "How to install Octave3 from source?"
date: 2009-06-30
forum: Education &amp; Science
---

### Post by serxyz on 2009-06-30
Hi there,

I am trying to install octave-3.2.0.tar.gz from source on DapperDrake (for more details plese see <http://ubuntuforums.org/showthread.php?t=1200824>). 

Has anybody been able to do it? I got error messages during compilation with "make":

==========================================
./DLD-FUNCTIONS/amd.cc: In function ‘octave_value_list Famd(const octave_value_list&, int)’:
./DLD-FUNCTIONS/amd.cc:174: error: ‘amd_malloc’ was not declared in this scope
./DLD-FUNCTIONS/amd.cc:175: error: ‘amd_free’ was not declared in this scope
./DLD-FUNCTIONS/amd.cc:176: error: ‘amd_calloc’ was not declared in this scope
./DLD-FUNCTIONS/amd.cc:177: error: ‘amd_realloc’ was not declared in this scope
./DLD-FUNCTIONS/amd.cc:178: error: ‘amd_printf’ was not declared in this scope
make[2]: *** [pic/amd.o] Error 1
make[2]: Leaving directory `/usr/local/src/octave-3.2.0/src'
make[1]: *** [src] Error 2
make[1]: Leaving directory `/usr/local/src/octave-3.2.0'
make: *** [all] Error 2
==========================================

Any suggestion?

Cheers,

S.**[B][B]**[/B][/B]

---

