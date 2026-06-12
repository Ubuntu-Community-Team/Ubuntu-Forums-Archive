---
title: "Problem developing static lib using KDevelop in Ubuntu"
date: 2008-12-05
forum: General Help
---

### Post by susin on 2008-12-05
Hi all,

      I have tried to create a static library .a (lib) in C++ using KDevelop in Ubuntu in the following way:

      1. First I have created a simple hello world project under C++->wxWidgets->Simple Hello wxWidgets Application.
 
      2. Next I right click on src and choose "Add Target".
    
      3. In "Add New Target" dialog I give Primary->Library, Prefix->noinst and filename as abcLib.

      4. Then I have pressed OK and then I have found libabcLib.a appears in Automake Manager.

      5. Next I have put the required source and header files under libabcLib.a.

      6. Then I have run "Run automake & friends and configure first"    

      7. I have encountered the following errors:

         src/Makefile.am:15: library used but `RANLIB' is undefined
         src/Makefile.am:15: The usual way to define `RANLIB' is to add  `AC_PROG_RANLIB'
         src/Makefile.am:15: to `configure.in' and run `autoconf' again.

      8. So I have added AC_PROG_RANLIB in configure.in and run "Run automake & friends and configure first" again.

      9. Then I have faced the following errors:
      
         configure.in:6: error: possibly undefined macro:  AC_LIBTOOL_DLOPEN If this token and others are legitimate, please use m4_pattern_allow. See the Autoconf documentation.
configure.in:7: error: possibly undefined macro: AC_PROG_LIBTOOL
make: *** [all] Error 1
*** Exited with status: 2 ***


      10. Then I deleted AC_LIBTOOL_DLOPEN and AC_PROG_LIBTOOL from configure.in and run "Build Target" again.

      11. This time it succeeds and I have found libabcLib.a is created in /debug/src path.

      12. I have then copied this lib to a specific location (say) /home/susin/Desktop/xyz.

      12. Next I have created my application in Kdevelop where I have planned to use this lib.

      13. In this application project I went to Project-> Project options-> Configure Options and gave the following under Linker Flags:

          -L/home/susin/Desktop/xyz -labcLib

      14. Then I have run "Build Target" and found linker errors regarding undefined reference of functions defined in abc lib.

      
      So my conclusion is either libabcLib.a is not created properly or it is not linked properly.

      Can somebody please help me for this issue...  


Thanks,
// susin

---

