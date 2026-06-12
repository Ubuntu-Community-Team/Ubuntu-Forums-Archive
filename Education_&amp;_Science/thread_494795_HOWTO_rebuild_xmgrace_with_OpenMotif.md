---
title: "HOWTO rebuild xmgrace with OpenMotif"
date: 2007-07-07
forum: Education &amp; Science
---

### Post by wirawan0 on 2007-07-07
I don't know where to put this posting. But I want to have this posted publicly so that at least somebody else can benefit from this. So here we go...


[B]HOW TO REBUILD XMGRACE WITH OPENMOTIF
[/B]

[I]Background
[/I]

Ubuntu 7.04 (feisty) build of xmgrace (with LessTif) turns out to be fatally buggy. The keyboard navigation is not working correctly. When we press 'Esc' on an open menu, it crashes. This is a major annoyance for me, since I would rather work with keyboard as much as possible. So I set out to rebuild xmgrace with OpenMotif with the hope of curing this sickness (and it did!).

My intent below is to use OpenMotif for xmgrace while at the same time not removing the stock LessTif package provided by Ubuntu, since it is needed by many other packages such as xpdf, etc.



[I]Howto
[/I]

**HACK 0:** Prior to building this package, I built and installed OpenMotif version 2.3.0 in the following subdirectory:

  /usr/local/openmotif-2.3.0

so I will use this library in building xmgrace instead of the "Ubuntu standard" LessTif 0.94. Somehow the interaction between LessTif and xmgrace causes crash in XmMenuEscape routine whenever I pressed Esc on an open menu item.

Get the package at [www.openmotif.org](www.openmotif.org) and build it according to the instruction. One hack that I had to do is comment out the `#if YY_MAIN' from openmotif-2.3.0/tools/wml/wmluiltok.c so that the program would compile. I was not sure if this is fully correct; but it worked for me:

```

~/BUILD/openmotif-2.3.0/tools/wml $ diff -u wmluiltok.c~ wmluiltok.c
--- wmluiltok.c~        2007-07-04 15:59:19.000000000 -0400
+++ wmluiltok.c 2007-07-04 15:59:19.000000000 -0400
@@ -1689,13 +1689,13 @@
        free( ptr );
        }
 
-#if YY_MAIN
+//#if YY_MAIN
 int main()
        {
        yylex();
        return 0;
        }
-#endif
+//#endif
 #line 183 "wmluiltok.l"

```

I started with the following packages from UBUNTU pool:

```

# -rw-r--r-- 1 wirawan wirawan   67460 2007-06-26 10:51 grace_5.1.21-1.diff
# -rw-r--r-- 1 wirawan wirawan     862 2007-06-26 10:51 grace_5.1.21-1.dsc
# -rw-r--r-- 1 wirawan wirawan 2474115 2007-06-26 10:51 grace_5.1.21.orig.tar.gz
# d677d9f3944564b0b74b7a8d3ea6ca0d  grace_5.1.21-1.diff
# c6fd0e95d98e4ed367ab9222bf27de63  grace_5.1.21-1.dsc
# db02dee3c68179c41452e652bd469bb9  grace_5.1.21.orig.tar.gz

```

These files can be found in

  [http://us.archive.ubuntu.com/ubuntu/pool/universe/g/grace/]("http://us.archive.ubuntu.com/ubuntu/pool/universe/g/grace/")

Expand the original tarball and apply the patch (*.diff file):

```

  /dir $ tar xzvf grace_5.1.21.orig.tar.gz
  /dir $ cd grace-5.1.21
  /dir/grace-5.1.21 $ patch  --verbose -p1 < ../grace_5.1.21-1.diff

```

**HACK 1:** Before running configure, I had to apply the following patch so that it looks for OpenMotif header files when figuring out the system settings:

```

~/BUILD $ diff -u origgrace/configure grace-5.1.21/configure
--- origgrace/configure2007-02-16 17:44:49.000000000 -0500
+++ grace-5.1.21/configure2007-07-06 17:34:52.000000000 -0400
@@ -15828,6 +15828,7 @@
 # Standard set of common directories for X headers.
 # Check X11 before X11Rn because it is often a symlink to the current release.
 ac_x_header_dirs='
+/usr/local/openmotif-2.3.0/include
 /usr/X11/include
 /usr/X11R6/include
 /usr/X11R5/include
@@ -17648,7 +17649,7 @@
 #endif
 
 _ACEOF
-if (eval "$ac_cpp conftest.$ac_ext") 2>&5 |
+if (eval "$ac_cpp $motif_library conftest.$ac_ext") 2>&5 |
   $EGREP "yes" >/dev/null 2>&1; then
   ice_cv_have_lesstif=yes
 else

```

Then now we can run the configure script:

```

  /dir/grace-5.1.21 $ ./configure --prefix=/usr/local/grace-5.1.21 --with-motif-library="-I/usr/local/openmotif-2.3.0/include -L/usr/local/openmotif-2.3.0/lib -lXm" --disable-xmhtml --with-helpviewer="firefox %s"

```

I disabled the XmHTML extension since that particular package was compiled with LessTif. Using firefox, as directed above, is fine with me.

**HACK 2:** After configuration, edit file Make.conf (line 100 in my case), so that it reads:

```

  GUI_FLAGS=-I/usr/local/openmotif-2.3.0/include

```

Unfortunately this is a flag that needs to be set manually so that gcc searches for OpenMotif include files *first* before LessTif files (which exist in standard search path). I have tried to set this via configure, yet there was no way to do it unless we meddle with configure.in (which I don't want to do).

We are then ready to build and install xmgrace! Good luck, and let me know if this work or not for you.

Notes-created: 20070707
Notes-updated: 20070707

Wirawan Purwanto

---

### Post by wgrant on 2007-07-16
If it is "fatally buggy" why haven't you filed a bug? It's not going to be fixed within Ubuntu unless we know there is something to be fixed! Please head over to [https://launchpad.net/ubuntu/+source/grace](https://launchpad.net/ubuntu/+source/grace) and file it.

---

### Post by wirawan0 on 2007-08-24
I have actually filed the bug report. But I put it under the lesstif2 package:

[https://bugs.launchpad.net/ubuntu/+source/lesstif2/+bug/124573](https://bugs.launchpad.net/ubuntu/+source/lesstif2/+bug/124573)

since I tend to think that it is LessTif's bug. But nobody ever cared to see/test it so far. :-(

Wirawan

---

