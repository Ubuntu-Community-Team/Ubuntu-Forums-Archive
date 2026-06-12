---
title: "Can't find the compiler"
date: 2005-09-10
forum: Desktop Environments
---

### Post by perlmonger on 2005-09-10
I'm a noob. That said, here's the problem, I've got gcc-3.3-base and gcc-4.0-base listed as installed packages. I'm running KUBUNTU 5.04 and have updated all packages. When I try to compile anything I get a "no suitabla c compiler found in PATH" error. What I need to know is how to find the path to the compiler so I can add it the PATH environment variable.

Here's my root path:

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/sur/bin/X11

'locate gcc' returns:

/var/lib/dpkg/info/libgcc1.shlibs
/var/lib/dpkg/info/libgcc1.list
/var/lib/dpkg/info/libgcc1.postinst
/var/lib/dpkg/info/libgcc1.postrm
/var/lib/dpkg/info/libgcc1.md5sums
/var/lib/dpkg/info/gcc-3.3-base.md5sums
/var/lib/dpkg/info/gcc-3.3-base.list
/var/lib/dpkg/info/gcc-4.0-base.md5sums
/var/lib/dpkg/info/gcc-4.0-base.list
/var/cache/apt/archives/gcc-3.3_1%3a3.3.5-8ubuntu2_i386.deb
/var/cache/apt/archives/gcc_4%3a3.3.5-1_i386.deb
/var/cache/apt/archives/libgcc1_1%3a4.0.0-7ubuntu6~5.04ubp1_i386.deb
/var/cache/apt/archives/gcc-4.0-base_4.0-0pre6ubuntu7_i386.deb
/usr/share/doc/libgcc1
/usr/share/doc/libgcc1/copyright
/usr/share/doc/libgcc1/changelog.Debian.gz
/usr/share/doc/gcc-3.3-base
/usr/share/doc/gcc-3.3-base/changelog.gz
/usr/share/doc/gcc-3.3-base/TODO.Debian
/usr/share/doc/gcc-3.3-base/copyright
/usr/share/doc/gcc-3.3-base/README.Debian.gz
/usr/share/doc/gcc-3.3-base/changelog.Debian.gz
/usr/share/doc/gcc-4.0-base
/usr/share/doc/gcc-4.0-base/changelog.Debian.gz
/usr/share/doc/gcc-4.0-base/README.Debian
/usr/share/doc/gcc-4.0-base/TODO.Debian
/usr/share/doc/gcc-4.0-base/copyright
/usr/share/doc/gcc-4.0-base/changelog.gz
/usr/share/man/man7/gfdl.7gcc.gz
/usr/share/man/man7/gpl.7gcc.gz
/usr/share/man/man7/fsf-funding.7gcc.gz
/usr/include/linux/compiler-gcc3.h
/usr/include/linux/compiler-gcc+.h
/usr/include/linux/compiler-gcc.h
/usr/include/linux/compiler-gcc2.h
/usr/lib/perl/5.8.4/linux/compiler-gcc+.ph
/usr/lib/perl/5.8.4/linux/compiler-gcc3.ph
/usr/lib/perl/5.8.4/linux/compiler-gcc2.ph
/usr/lib/perl/5.8.4/linux/compiler-gcc.ph
/usr/lib/libgccpp.so.1.0.2
/usr/lib/libgccpp.so.1
/usr/lib/gcc-lib/var/lib/dpkg/info/libgcc1.shlibs
/var/lib/dpkg/info/libgcc1.list
/var/lib/dpkg/info/libgcc1.postinst
/var/lib/dpkg/info/libgcc1.postrm
/var/lib/dpkg/info/libgcc1.md5sums
/var/lib/dpkg/info/gcc-3.3-base.md5sums
/var/lib/dpkg/info/gcc-3.3-base.list
/var/lib/dpkg/info/gcc-4.0-base.md5sums
/var/lib/dpkg/info/gcc-4.0-base.list
/var/cache/apt/archives/gcc-3.3_1%3a3.3.5-8ubuntu2_i386.deb
/var/cache/apt/archives/gcc_4%3a3.3.5-1_i386.deb
/var/cache/apt/archives/libgcc1_1%3a4.0.0-7ubuntu6~5.04ubp1_i386.deb
/var/cache/apt/archives/gcc-4.0-base_4.0-0pre6ubuntu7_i386.deb
/usr/share/doc/libgcc1
/usr/share/doc/libgcc1/copyright
/usr/share/doc/libgcc1/changelog.Debian.gz
/usr/share/doc/gcc-3.3-base
/usr/share/doc/gcc-3.3-base/changelog.gz
/usr/share/doc/gcc-3.3-base/TODO.Debian
/usr/share/doc/gcc-3.3-base/copyright
/usr/share/doc/gcc-3.3-base/README.Debian.gz
/usr/share/doc/gcc-3.3-base/changelog.Debian.gz
/usr/share/doc/gcc-4.0-base
/usr/share/doc/gcc-4.0-base/changelog.Debian.gz
/usr/share/doc/gcc-4.0-base/README.Debian
/usr/share/doc/gcc-4.0-base/TODO.Debian
/usr/share/doc/gcc-4.0-base/copyright
/usr/share/doc/gcc-4.0-base/changelog.gz
/usr/share/man/man7/gfdl.7gcc.gz
/usr/share/man/man7/gpl.7gcc.gz/var/lib/dpkg/info/libgcc1.shlibs
/var/lib/dpkg/info/libgcc1.list
/var/lib/dpkg/info/libgcc1.postinst
/var/lib/dpkg/info/libgcc1.postrm
/var/lib/dpkg/info/libgcc1.md5sums
/var/lib/dpkg/info/gcc-3.3-base.md5sums
/var/lib/dpkg/info/gcc-3.3-base.list
/var/lib/dpkg/info/gcc-4.0-base.md5sums
/var/lib/dpkg/info/gcc-4.0-base.list
/var/cache/apt/archives/gcc-3.3_1%3a3.3.5-8ubuntu2_i386.deb
/var/cache/apt/archives/gcc_4%3a3.3.5-1_i386.deb
/var/cache/apt/archives/libgcc1_1%3a4.0.0-7ubuntu6~5.04ubp1_i386.deb
/var/cache/apt/archives/gcc-4.0-base_4.0-0pre6ubuntu7_i386.deb
/usr/share/doc/libgcc1
/usr/share/doc/libgcc1/copyright
/usr/share/doc/libgcc1/changelog.Debian.gz
/usr/share/doc/gcc-3.3-base
/usr/share/doc/gcc-3.3-base/changelog.gz
/usr/share/doc/gcc-3.3-base/TODO.Debian
/usr/share/doc/gcc-3.3-base/copyright
/usr/share/doc/gcc-3.3-base/README.Debian.gz
/usr/share/doc/gcc-3.3-base/changelog.Debian.gz
/usr/share/doc/gcc-4.0-base
/usr/share/doc/gcc-4.0-base/changelog.Debian.gz
/usr/share/doc/gcc-4.0-base/README.Debian
/usr/share/doc/gcc-4.0-base/TODO.Debian
/usr/share/doc/gcc-4.0-base/copyright
/usr/share/doc/gcc-4.0-base/changelog.gz
/usr/share/man/man7/gfdl.7gcc.gz
/usr/share/man/man7/gpl.7gcc.gz
/usr/share/man/man7/fsf-funding.7gcc.gz
/usr/include/linux/compiler-gcc3.h
/usr/include/linux/compiler-gcc+.h
/usr/include/linux/compiler-gcc.h
/usr/include/linux/compiler-gcc2.h
/usr/lib/perl/5.8.4/linux/compiler-gcc+.ph
/usr/lib/perl/5.8.4/linux/compiler-gcc3.ph
/usr/lib/perl/5.8.4/linux/compiler-gcc2.ph
/usr/lib/perl/5.8.4/linux/compiler-gcc.ph
/usr/lib/libgccpp.so.1.0.2
/usr/lib/libgccpp.so.1
/usr/lib/gcc-lib
/usr/lib/gcc-lib/i486-linux
/usr/lib/gcc-lib/i486-linux/3.3.5
/usr/lib/gcc-lib/i486-linux/3.3.5/cc1
/usr/lib/libstlport_gcc.so.4.6
/usr/lib/openoffice/program/libcppuhelpergcc3.so.3.1.0
/usr/lib/openoffice/program/libcomphelp3gcc3.so
/usr/lib/openoffice/program/libgcc3_uno.so
/usr/lib/openoffice/program/libsalhelpergcc3.so.3.1.0
/usr/lib/openoffice/program/libi18nregexpgcc3.so
/usr/lib/openoffice/program/libi18nutilgcc3.so
/usr/lib/openoffice/program/libucbhelper2gcc3.so
/usr/lib/openoffice/program/libvos3gcc3.so
/usr/lib/openoffice/program/libcppuhelpergcc3.so.3
/usr/lib/openoffice/program/libsalhelpergcc3.so.3
/usr/X11R6/man/man1/gccmakedep.1x.gz
/usr/X11R6/bin/gccmakedep
/lib/libgcc_s.so.1

/usr/share/man/man7/fsf-funding.7gcc.gz
/usr/include/linux/compiler-gcc3.h
/usr/include/linux/compiler-gcc+.h
/usr/include/linux/compiler-gcc.h
/usr/include/linux/compiler-gcc2.h
/usr/lib/perl/5.8.4/linux/compiler-gcc+.ph
/usr/lib/perl/5.8.4/linux/compiler-gcc3.ph
/usr/lib/perl/5.8.4/linux/compiler-gcc2.ph
/usr/lib/perl/5.8.4/linux/compiler-gcc.ph
/usr/lib/libgccpp.so.1.0.2
/usr/lib/libgccpp.so.1
/usr/lib/gcc-lib
/usr/lib/gcc-lib/i486-linux
/usr/lib/gcc-lib/i486-linux/3.3.5
/usr/lib/gcc-lib/i486-linux/3.3.5/cc1
/usr/lib/libstlport_gcc.so.4.6
/usr/lib/openoffice/program/libcppuhelpergcc3.so.3.1.0
/usr/lib/openoffice/program/libcomphelp3gcc3.so
/usr/lib/openoffice/program/libgcc3_uno.so
/usr/lib/openoffice/program/libsalhelpergcc3.so.3.1.0
/usr/lib/openoffice/program/libi18nregexpgcc3.so
/usr/lib/openoffice/program/libi18nutilgcc3.so
/usr/lib/openoffice/program/libucbhelper2gcc3.so
/usr/lib/openoffice/program/libvos3gcc3.so
/usr/lib/openoffice/program/libcppuhelpergcc3.so.3
/usr/lib/openoffice/program/libsalhelpergcc3.so.3
/usr/X11R6/man/man1/gccmakedep.1x.gz
/usr/X11R6/bin/gccmakedep
/lib/libgcc_s.so.1

/usr/lib/gcc-lib/i486-linux
/usr/lib/gcc-lib/i486-linux/3.3.5
/usr/lib/gcc-lib/i486-linux/3.3.5/cc1
/usr/lib/libstlport_gcc.so.4.6
/usr/lib/openoffice/program/libcppuhelpergcc3.so.3.1.0
/usr/lib/openoffice/program/libcomphelp3gcc3.so
/usr/lib/openoffice/program/libgcc3_uno.so
/usr/lib/openoffice/program/libsalhelpergcc3.so.3.1.0
/usr/lib/openoffice/program/libi18nregexpgcc3.so
/usr/lib/openoffice/program/libi18nutilgcc3.so
/usr/lib/openoffice/program/libucbhelper2gcc3.so
/usr/lib/openoffice/program/libvos3gcc3.so
/usr/lib/openoffice/program/libcppuhelpergcc3.so.3
/usr/lib/openoffice/program/libsalhelpergcc3.so.3
/usr/X11R6/man/man1/gccmakedep.1x.gz
/usr/X11R6/bin/gccmakedep
/lib/libgcc_s.so.1

Can someone help me get my PATH pointed to the right path to the compiler?

Thanks

---

### Post by DarkT on 2005-09-10
It would seem that although you have the base package installed you don't have the actual compiler installed. In synaptic (or however you get your pacakges from the repositories) do a search for / install "build essentials" which will give you the basics you need.

---

### Post by perlmonger on 2005-09-11
Thanks, but I searched for "build essentials" and it returned nothing. Can someone tell me what packages I need so I can get them manually?

Thanks

---

### Post by rusi_pathan on 2005-09-11
'sudo apt-get install build-essential'

See [http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by tseliot on 2005-09-11
[QUOTE=perlmonger]I'm a noob. That said, here's the problem, I've got gcc-3.3-base and gcc-4.0-base listed as installed packages. I'm running KUBUNTU 5.04 and have updated all packages.[/QUOTE]

Make sure you have installed both gcc-3.3 and gcc-4.0 [COLOR=Red](NOT ONLY the base package)[/COLOR]

And make sure you have enabled all the repositories (as described in Ubuntu starter's guide)

---

### Post by perlmonger on 2005-09-11
[QUOTE=rusi_pathan]'sudo apt-get install build-essential'

See [http://ubuntuguide.org/](http://ubuntuguide.org/)[/QUOTE]
 That did it, thanks guys!

---

