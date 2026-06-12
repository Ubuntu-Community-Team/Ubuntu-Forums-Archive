---
title: "patch file format"
date: 2009-01-11
forum: General Help
---

### Post by yinglcs2 on 2009-01-11
Is this file a valid patch file format?


```

diff -r -c -b Python-2.4.5/Makefile.pre.in Python-2.4.5-android/Makefile.pre.in
*** Python-2.4.5/Makefile.pre.in Sun Oct  8 19:41:25 2006
--- Python-2.4.5-android/Makefile.pre.in Fri Dec 19 10:02:17 2008
***************
*** 166,171 ****
--- 166,172 ----
  
  PYTHON=  python$(EXE)
  BUILDPYTHON= python$(BUILDEXE)
+ HOSTPYTHON= ./$(BUILDPYTHON)
  
  # === Definitions added by makesetup ===
  
***************
*** 192,197 ****
--- 193,199 ----
  ##########################################################################
  # Parser
  PGEN=  Parser/pgen$(EXE)
+ HOSTPGEN=       $(PGEN)
  
  POBJS=  \
    Parser/acceler.o \
***************
*** 324,331 ****
  # Build the shared modules
  sharedmods: $(BUILDPYTHON)
   case $$MAKEFLAGS in \
!  *-s*) $(RUNSHARED) CC='$(CC)' LDSHARED='$(BLDSHARED)' OPT='$(OPT)' ./$(BUILDPYTHON) -E $(srcdir)/setup.py -q build;; \
!  *) $(RUNSHARED) CC='$(CC)' LDSHARED='$(BLDSHARED)' OPT='$(OPT)' ./$(BUILDPYTHON) -E $(srcdir)/setup.py build;; \
   esac
  
  # buildno should really depend on something like LIBRARY_SRC
--- 326,333 ----
  # Build the shared modules
  sharedmods: $(BUILDPYTHON)
   case $$MAKEFLAGS in \
!  *-s*) $(RUNSHARED) CC='$(CC)' LDSHARED='$(BLDSHARED)' OPT='$(OPT)' $(HOSTPYTHON) -E $(srcdir)/setup.py -q build;; \
!  *) $(RUNSHARED) CC='$(CC)' LDSHARED='$(BLDSHARED)' OPT='$(OPT)' $(HOSTPYTHON) -E $(srcdir)/setup.py build;; \
   esac
  
  # buildno should really depend on something like LIBRARY_SRC
***************
*** 455,461 ****
  
  
  $(GRAMMAR_H) $(GRAMMAR_C): $(PGEN) $(GRAMMAR_INPUT)
!   -$(PGEN) $(GRAMMAR_INPUT) $(GRAMMAR_H) $(GRAMMAR_C)
  
  $(PGEN): $(PGENOBJS)
    $(CC) $(OPT) $(LDFLAGS) $(PGENOBJS) $(LIBS) -o $(PGEN)
--- 457,463 ----
  
  
  $(GRAMMAR_H) $(GRAMMAR_C): $(PGEN) $(GRAMMAR_INPUT)
!   -$(HOSTPGEN) $(GRAMMAR_INPUT) $(GRAMMAR_H) $(GRAMMAR_C)
  
  $(PGEN): $(PGENOBJS)
    $(CC) $(OPT) $(LDFLAGS) $(PGENOBJS) $(LIBS) -o $(PGEN)
***************
*** 748,767 ****
    done; \
   done
   $(INSTALL_DATA) $(srcdir)/LICENSE $(DESTDIR)$(LIBDEST)/LICENSE.txt
!  PYTHONPATH=$(DESTDIR)$(LIBDEST)  $(RUNSHARED) \
!   ./$(BUILDPYTHON) -Wi -tt $(DESTDIR)$(LIBDEST)/compileall.py \
    -d $(LIBDEST) -f \
    -x 'badsyntax|site-packages' $(DESTDIR)$(LIBDEST)
!  PYTHONPATH=$(DESTDIR)$(LIBDEST) $(RUNSHARED) \
!   ./$(BUILDPYTHON) -Wi -tt -O $(DESTDIR)$(LIBDEST)/compileall.py \
    -d $(LIBDEST) -f \
    -x 'badsyntax|site-packages' $(DESTDIR)$(LIBDEST)
   -PYTHONPATH=$(DESTDIR)$(LIBDEST)  $(RUNSHARED) \
!   ./$(BUILDPYTHON) -Wi -t $(DESTDIR)$(LIBDEST)/compileall.py \
    -d $(LIBDEST)/site-packages -f \
    -x badsyntax $(DESTDIR)$(LIBDEST)/site-packages
   -PYTHONPATH=$(DESTDIR)$(LIBDEST) $(RUNSHARED) \
!   ./$(BUILDPYTHON) -Wi -t -O $(DESTDIR)$(LIBDEST)/compileall.py \
    -d $(LIBDEST)/site-packages -f \
    -x badsyntax $(DESTDIR)$(LIBDEST)/site-packages
  
--- 750,769 ----
    done; \
   done
   $(INSTALL_DATA) $(srcdir)/LICENSE $(DESTDIR)$(LIBDEST)/LICENSE.txt
!  -PYTHONPATH=$(DESTDIR)$(LIBDEST)  $(RUNSHARED) \
!   $(HOSTPYTHON) -Wi -tt $(DESTDIR)$(LIBDEST)/compileall.py \
    -d $(LIBDEST) -f \
    -x 'badsyntax|site-packages' $(DESTDIR)$(LIBDEST)
!  -PYTHONPATH=$(DESTDIR)$(LIBDEST) $(RUNSHARED) \
!   $(HOSTPYTHON) -Wi -tt -O $(DESTDIR)$(LIBDEST)/compileall.py \
    -d $(LIBDEST) -f \
    -x 'badsyntax|site-packages' $(DESTDIR)$(LIBDEST)
   -PYTHONPATH=$(DESTDIR)$(LIBDEST)  $(RUNSHARED) \
!   $(HOSTPYTHON) -Wi -t $(DESTDIR)$(LIBDEST)/compileall.py \
    -d $(LIBDEST)/site-packages -f \
    -x badsyntax $(DESTDIR)$(LIBDEST)/site-packages
   -PYTHONPATH=$(DESTDIR)$(LIBDEST) $(RUNSHARED) \
!   $(HOSTPYTHON) -Wi -t -O $(DESTDIR)$(LIBDEST)/compileall.py \
    -d $(LIBDEST)/site-packages -f \
    -x badsyntax $(DESTDIR)$(LIBDEST)/site-packages
  
***************
*** 856,862 ****
  # Install the dynamically loadable modules
  # This goes into $(exec_prefix)
  sharedinstall:
!  $(RUNSHARED) ./$(BUILDPYTHON) -E $(srcdir)/setup.py install \
       --prefix=$(prefix) \
    --install-scripts=$(BINDIR) \
    --install-platlib=$(DESTSHARED) \
--- 858,864 ----
  # Install the dynamically loadable modules
  # This goes into $(exec_prefix)
  sharedinstall:
!  $(RUNSHARED) $(HOSTPYTHON) -E $(srcdir)/setup.py install \
       --prefix=$(prefix) \
    --install-scripts=$(BINDIR) \
    --install-platlib=$(DESTSHARED) \
diff -r -c -b Python-2.4.5/Modules/pwdmodule.c Python-2.4.5-android/Modules/pwdmodule.c
*** Python-2.4.5/Modules/pwdmodule.c Wed Sep 27 21:17:32 2006
--- Python-2.4.5-android/Modules/pwdmodule.c Fri Dec 19 10:26:14 2008
***************
*** 77,83 ****
  #ifdef __VMS
   SETS(setIndex++, "");
  #else
!  SETS(setIndex++, p->pw_gecos);
  #endif
   SETS(setIndex++, p->pw_dir);
   SETS(setIndex++, p->pw_shell);
--- 77,83 ----
  #ifdef __VMS
   SETS(setIndex++, "");
  #else
!  SETS(setIndex++, "");//p->pw_gecos);
  #endif
   SETS(setIndex++, p->pw_dir);
   SETS(setIndex++, p->pw_shell);
diff -r -c -b Python-2.4.5/Modules/socketmodule.c Python-2.4.5-android/Modules/socketmodule.c
*** Python-2.4.5/Modules/socketmodule.c Tue Oct 10 18:20:41 2006
--- Python-2.4.5-android/Modules/socketmodule.c Fri Dec 19 17:51:36 2008
***************
*** 61,66 ****
--- 61,67 ----
  
  */
  
+ #define INET_ADDRSTRLEN 16
  #ifdef __APPLE__
    /*
     * inet_aton is not available on OSX 10.3, yet we want to use a binary
diff -r -c -b Python-2.4.5/Objects/fileobject.c Python-2.4.5-android/Objects/fileobject.c
*** Python-2.4.5/Objects/fileobject.c Tue Jan 23 16:09:19 2007
--- Python-2.4.5-android/Objects/fileobject.c Fri Dec 19 16:47:32 2008
***************
*** 1,5 ****
--- 1,6 ----
  /* File object implementation */
  
+ #include "/android_src/bionic/libc/stdio/clrerr.c"
  #include "Python.h"
  #include "structmember.h"

diff -r -c -b Python-2.4.5/Python/pystrtod.c Python-2.4.5-android/Python/pystrtod.c
*** Python-2.4.5/Python/pystrtod.c Tue Jun  8 20:52:54 2004
--- Python-2.4.5-android/Python/pystrtod.c Fri Dec 19 10:18:11 2008
***************
*** 54,61 ****
  
   fail_pos = NULL;
  
!  locale_data = localeconv();
!  decimal_point = locale_data->decimal_point;
   decimal_point_len = strlen(decimal_point);
  
   assert(decimal_point_len != 0);
--- 54,61 ----
  
   fail_pos = NULL;
  
!  //locale_data = localeconv();
!  decimal_point = '.';//locale_data->decimal_point;
   decimal_point_len = strlen(decimal_point);
  
   assert(decimal_point_len != 0);
***************
*** 218,225 ****
  
   PyOS_snprintf(buffer, buf_len, format, d);
  
!  locale_data = localeconv();
!  decimal_point = locale_data->decimal_point;
   decimal_point_len = strlen(decimal_point);
  
   assert(decimal_point_len != 0);
--- 218,225 ----
  
   PyOS_snprintf(buffer, buf_len, format, d);
  
!  //locale_data = localeconv();
!  decimal_point = '.';//locale_data->decimal_point;
   decimal_point_len = strlen(decimal_point);
  
   assert(decimal_point_len != 0);
diff -r -c -b Python-2.4.5/setup.py Python-2.4.5-android/setup.py
*** Python-2.4.5/setup.py Sun Oct  8 19:41:25 2006
--- Python-2.4.5-android/setup.py Fri Dec 19 17:26:29 2008
***************
*** 15,21 ****
  from distutils.command.install_lib import install_lib
  
  # This global variable is used to hold the list of modules to be disabled.
! disabled_module_list = []
  
  def add_dir_to_list(dirlist, dir):
      """Add the directory 'dir' to the list 'dirlist' (at the front) if
--- 15,33 ----
  from distutils.command.install_lib import install_lib
  
  # This global variable is used to hold the list of modules to be disabled.
! disabled_module_list = [
!     '_ctypes',
!     '_curses',
!     '_curses_panel',
!     '_locale',
!     '_ssl',
!     'crypt',
!     'linuxaudiodev',
!     'nis',
!     'ossaudiodev',
!     'readline',
!     'zlib',
!     ]
  
  def add_dir_to_list(dirlist, dir):
      """Add the directory 'dir' to the list 'dirlist' (at the front) if
***************
*** 199,204 ****
--- 211,218 ----
              self.announce('WARNING: skipping import check for Cygwin-based "%s"'
                  % ext.name)
              return
+         if os.environ.get('CROSS_COMPILE') == 'yes':
+             return
          ext_filename = os.path.join(
              self.build_lib,
              self.get_ext_filename(self.get_ext_fullname(ext.name)))

```

If yes, where should I put the patch file and how to apply the patch?

Thank you.

---

### Post by spiderbatdad on 2009-01-11
Here is an example:
[http://www.lysium.de/blog/index.php?/archives/229-Installing-Python-2.6-on-Ubuntu-8.04.html](http://www.lysium.de/blog/index.php?/archives/229-Installing-Python-2.6-on-Ubuntu-8.04.html)
```
--- Python-2.6-orig/setup.py	2008-09-30 02:15:45.000000000 +0200
+++ Python-2.6/setup.py	2008-11-04 17:01:04.000000000 +0100
@@ -987,7 +987,7 @@
         # the more recent berkeleydb's db.h file first in the include path
         # when attempting to compile and it will fail.
         f = "/usr/include/db.h"
-        if os.path.exists(f) and not db_incs:
+        if False and os.path.exists(f) and not db_incs:
             data = open(f).read()
             m = re.search(r"#s*define\s+HASHVERSION\s+2\s*", data)
             if m is not None:
@@ -1004,7 +1004,8 @@
             else:
                 missing.append('bsddb185')
         else:
-            missing.append('bsddb185')
+			pass
+#             missing.append('bsddb185')
 
         # The standard Unix dbm module:
         if platform not in ['cygwin']:
@@ -1324,7 +1325,8 @@
             # SunOS specific modules
             exts.append( Extension('sunaudiodev', ['sunaudiodev.c']) )
         else:
-            missing.append('sunaudiodev')
+			pass
+#             missing.append('sunaudiodev')
 
         if platform == 'darwin' and ("--disable-toolbox-glue" not in
                 sysconfig.get_config_var("CONFIG_ARGS")):
```

---

### Post by yinglcs2 on 2009-01-11
Okay.  I get the 'patch' from this site:
[http://www.damonkohler.com/2008/12/python-on-android.html](http://www.damonkohler.com/2008/12/python-on-android.html)

It said 'Apply the following patch to the Python source.'.
But Can you please tell me how to apply this patch?

Thank you.

---

