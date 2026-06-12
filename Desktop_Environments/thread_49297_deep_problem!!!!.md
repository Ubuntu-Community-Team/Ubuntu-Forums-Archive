---
title: "deep problem!!!!"
date: 2005-07-15
forum: Desktop Environments
---

### Post by yoshic on 2005-07-15
hi guy i've got a big problem, accidentaly i remove the library libgdbm3, but not only remove that one, also lots of another  ones, and i could remember a few, some one can help me  whit the dependences?????

---

### Post by hydra on 2005-07-15
Don't know right but maybe u could try to update with apt-get this libraries:
```

libc6 libc6-dev libcomerr2 libdb1-compat libgdbm3 libkrb53 libncurses5 libpq3 libreadline4 libssl0.9.7 linux-kernel-headers locales tcl8.4 tk8.4 zlib1g
```


at least for the one u remember
```

#apt-get install libgdbm3
#apt-get install libgdbm3-dev

```

just in case u delete them

hope it helps

---

### Post by jasmuz on 2005-07-15
Just sudo apt-get install libgdbm3, and that should download the other packages that are dependencies.

---

### Post by hydra on 2005-07-15
I found a package that may help u....[COLOR=red]I THINK U SHOULD DO THIS JUST AS LAST RESOURCE[/COLOR] 

[i386chroot.tar.gz](http://rufus.hackish.org/~rufus/files/i386chroot.tar.bz)

***First make sure you do not any any of the ia32-libs installed (ia32-libs, ia32-libs-dev, ia32-libs-openoffice.org)****

then just go, being root:
```
$ cd /emul

# extract the archive
$ tar jxvf i386chroot.tar.bz

# setup networking
$ cp /etc/resolv.conf /emul/chroot/etc/resolv.conf

# edit the chroot's sources.list to point at your favorite
$ editor /emul/chroot/etc/apt/sources.list

# actually chroot into our new area
$ chroot /emul/chroot

# pull down a package list
$ apt-get update

# go wild
$ apt-get install libfoobar

# it's all working, lets exit out of the chroot
exit

# now replace /emul/ia32-linux/ with our new one
rm -rf /emul/ia32-linux
mv /emul/chroot /emul/ia32-linux
```

and this are the packages contained in it:
```
|/ Name                   Version        Description
+++-======================-==============-===============================================================
ii  apt                    0.5.27         Advanced front-end for dpkg
ii  apt-utils              0.5.27         APT utility programs
ii  base-files             3.1            Debian base system miscellaneous files
ii  base-passwd            3.5.8          Debian base system master password and group files
ii  bash                   3.0-8          The GNU Bourne Again SHell
ii  coreutils              5.2.1-2        The GNU core utilities
ii  debconf                1.4.39         Debian configuration management system
ii  debconf-i18n           1.4.39         full internationalization support for debconf
ii  debianutils            2.10.3         Miscellaneous utilities specific to Debian
ii  dialog                 1.0-20040920-1 Displays user-friendly dialog boxes from shell scripts
ii  dpkg                   1.10.23        Package maintenance system for Debian
ii  dselect                1.10.23        a user tool to manage Debian packages
ii  gcc-3.3-base           3.3.5-1        The GNU Compiler Collection (base package)
ii  grep                   2.5.1.ds1-3.2  GNU grep, egrep and fgrep
ii  gzip                   1.3.5-9        The GNU compression utility
ii  libacl1                2.2.26-1       Access control list shared library
ii  libattr1               2.4.18-1       Extended attribute shared library
ii  libc6                  2.3.2.ds1-18   GNU C Library: Shared libraries and Timezone data
ii  libcap1                1.10-14        support for getting/setting POSIX.1e capabilities
ii  libdb1-compat          2.1.3-7        The Berkeley database routines [glibc 2.0/2.1 compatibility]
ii  libdb3                 3.2.9-20       Berkeley v3 Database Libraries [runtime]
ii  libdb4.2               4.2.52-17      Berkeley v4.2 Database Libraries [runtime]
ii  libgcc1                3.4.2-3        GCC support library
ii  libgdbm3               1.8.3-2        GNU dbm database routines (runtime version)
ii  liblocale-gettext-perl 1.01-17        Using libc functions for internationalization in Perl
ii  libncurses5            5.4-4          Shared libraries for terminal handling
ii  libncursesw5           5.4-4          Shared libraries for terminal handling (wide character support)
ii  libpam-modules         0.76-22        Pluggable Authentication Modules for PAM
ii  libpam-runtime         0.76-22        Runtime support for the PAM library
ii  libpam0g               0.76-22        Pluggable Authentication Modules library
ii  libstdc++5             3.3.5-1        The GNU Standard C++ Library v3
pi  libtext-charwidth-perl 0.04-1         get display widths of characters on the terminal
ii  libtext-iconv-perl     1.2-3          Convert between character sets in Perl
ii  libtext-wrapi18n-perl  0.06-1         internationalized substitute of Text::Wrap
ii  login                  4.0.3-30.2     System login tools
ii  mawk                   1.3.3-11       a pattern scanning and text processing language
ii  passwd                 4.0.3-30.2     Change and administer password and group data
ii  perl                   5.8.4-2.3      Larry Wall's Practical Extraction and Report Language
ii  perl-base              5.8.4-2.3      The Pathologically Eclectic Rubbish Lister
ii  perl-modules           5.8.4-2.3      Core Perl modules
ii  sed                    4.1.2-1        The GNU sed stream editor
ii  slang1a-utf8           1.4.9dbs-8     The S-Lang programming library with utf8 support
ii  sysv-rc                2.86-5         Standard boot mechanism using symlinks in /etc/rc?.d
ii  tar                    1.14-2         GNU tar
ii  util-linux             2.12-10        Miscellaneous system utilities
ii  zlib1g                 1.2.2-1        compression library - runtime
```

---

### Post by tomchuk on 2005-07-15
Reinstalling ubuntu-base and ubuntu-desktop should get you back to a reasonable state.

---

### Post by yoshic on 2005-07-16
thanks hydra, i could resolve this messs,   \\:D/  thanks!! thanks!! :-)  :razz:

---

### Post by hydra on 2005-07-16
Yep man no prob im glad it helps....

---

