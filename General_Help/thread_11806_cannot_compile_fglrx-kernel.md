---
title: "cannot compile fglrx-kernel"
date: 2005-01-19
forum: General Help
---

### Post by cantas on 2005-01-19
Hi,

when trying to compile fglrx-kernel module this problem appears:

root@portatile-ubuntu:/usr/src/linux-2.6.10 # make-kpkg --revision 1 --added-modules=fglrx-kernel modules_image
for module in /usr/src/modules/fglrx-kernel ; do                       \
          if test -d  $module; then                                \
    (cd $module;                                          \
              if ./debian/rules KVERS="2.6.10-win4lin" KSRC="/usr/src/linux-2.6.10" \
                             KMAINT="Unknown Kernel Package Maintainer" KEMAIL="unknown@unconfigured.in.etc.kernel-pkg.conf"      \
                             KPKG_DEST_DIR="/usr/src/linux-2.6.10/.."       \
                             KPKG_MAINTAINER="Unknown Kernel Package Maintainer"        \
                             KPKG_EXTRAV_ARG=""        \
                             ARCH="i386"                  \
                             KDREV="1" kdist_image; then    \
                  echo "Module $module processed fine";            \
              else                                                  \
                   echo "Module $module failed.";                  \
                   if [ "X" != "X" ]; then      \
                      echo "Perhaps $module does not understand --rootcmd?";  \
                      echo "If you see messages that indicate that it is not"; \
                      echo "in fact being built as root, please file a bug ";  \
                      echo "against $module.";                     \
                   fi;                                              \
                   echo "Hit return to Continue";                   \
         read ans;                                        \
              fi;                                                   \
     );                                                    \
  fi;                                                      \
        done
make[1]: Entering directory `/usr/src/modules/fglrx-kernel'
./debian/rules:77: *** missing separator (did you mean TAB instead of 8 spaces?).  Stop.
make[1]: Leaving directory `/usr/src/modules/fglrx-kernel'
Module /usr/src/modules/fglrx-kernel failed.
Hit return to Continue

Then I removed those 8 spaces and put a tab.

root@portatile-ubuntu:/usr/src/linux-2.6.10 # make-kpkg --revision 1 --added-modules=fglrx-kernel modules_image
for module in /usr/src/modules/fglrx-kernel ; do                       \
          if test -d  $module; then                                \
    (cd $module;                                          \
              if ./debian/rules KVERS="2.6.10-win4lin" KSRC="/usr/src/linux-2.6.10" \
                             KMAINT="Unknown Kernel Package Maintainer" KEMAIL="unknown@unconfigured.in.etc.kernel-pkg.conf"      \
                             KPKG_DEST_DIR="/usr/src/linux-2.6.10/.."       \
                             KPKG_MAINTAINER="Unknown Kernel Package Maintainer"        \
                             KPKG_EXTRAV_ARG=""        \
                             ARCH="i386"                  \
                             KDREV="1" kdist_image; then    \
                  echo "Module $module processed fine";            \
              else                                                  \
                   echo "Module $module failed.";                  \
                   if [ "X" != "X" ]; then      \
                      echo "Perhaps $module does not understand --rootcmd?";  \
                      echo "If you see messages that indicate that it is not"; \
                      echo "in fact being built as root, please file a bug ";  \
                      echo "against $module.";                     \
                   fi;                                              \
                   echo "Hit return to Continue";                   \
         read ans;                                        \
              fi;                                                   \
     );                                                    \
  fi;                                                      \
        done
make[1]: Entering directory `/usr/src/modules/fglrx-kernel'
echo "ROOT_CMD = "
ROOT_CMD =
/usr/bin/make -w -f debian/rules binary_modules
make[2]: Entering directory `/usr/src/modules/fglrx-kernel'
# select which makefile to use.
rm -f /usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x/Makefile || true
cd /usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x ; \
ln -s Makefile.kbuild Makefile ; \
cd .. ; \

#nothing here anymore
touch configure-stamp
if [ -f /usr/src/modules/fglrx-kernel/debian/control.template ]; then \
        cp  /usr/src/modules/fglrx-kernel/debian/control.template /usr/src/modules/fglrx-kernel/debian/control; \
fi
dh_testdir
dh_testroot
PATCHLEVEL = 6
Kernel compiler version : 3.3.5
Detected compiler version : 3.3.5
Using compiler gcc-3.3 version 3.3.5
touch /usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x/gcc-check
touch /usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x/cc-sanity-check
## Main Make ##
IGNORE_CC_MISMATCH=1 CC="gcc-3.3"  /usr/bin/make -C /usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x -f Makefile SYSSRC=/usr/src/linux-2.6.10   KBUILD_PARAMS="-C /usr/src/linux-2.6.10 SUBDIRS=/usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x"
make[3]: Entering directory `/usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x'
make[3]: Makefile: No such file or directory
make[3]: *** No rule to make target `Makefile'.  Stop.
make[3]: Leaving directory `/usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x'
make[2]: *** [build-stamp] Error 2
make[2]: Leaving directory `/usr/src/modules/fglrx-kernel'
make[1]: *** [kdist_image] Error 2
make[1]: Leaving directory `/usr/src/modules/fglrx-kernel'
Module /usr/src/modules/fglrx-kernel failed.
Hit return to Continue

It seems that something deletes the makefile put in 2.6.x folder. if I comment line 78 of debian/rules something works but the process stops all the same...

What can I do?
Thank you
Stefano

---

### Post by gothfox on 2005-02-08
You were half way there. Although, judging on the obvious bugs I wonder if anybody even tried to build the package before uploading it to the repository as it is broken completely.

Anyway, I managed to build the package (see diff below) but I didn't yet see if the resulting module actually works.

[http://bah.spb.su/~fox/unsorted/linux/fglrx-kernel-source.diff](http://bah.spb.su/~fox/unsorted/linux/fglrx-kernel-source.diff)

---

