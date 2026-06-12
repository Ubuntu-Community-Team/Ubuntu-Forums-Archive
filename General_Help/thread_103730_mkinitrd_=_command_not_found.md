---
title: "mkinitrd = command not found"
date: 2005-12-14
forum: General Help
---

### Post by carlosqueso on 2005-12-14
When i try to use mkinitrd to manually make an initrd for my new kernel, I get an command not found error.  Is there something I need to install to get it to work?

---

### Post by ape on 2005-12-14
mkinitrd is in the initrd-tools package.  You may also want to take a look at initramfs-tools which includes mkinitramfs.

---

### Post by az on 2005-12-14
dora@dora:~$ apt-cache show initrd-tools
Package: initrd-tools
Priority: optional
Section: utils
Installed-Size: 176
Maintainer: Debian kernel team <debian-kernel@lists.debian.org>
Architecture: all
Version: 0.1.78ubuntu2
Depends: coreutils | fileutils (>= 4.1.9) | stat (>= 3.0), cpio, cramfsprogs (>= 1.1-4), dash, util-linux (>= 2.11b-3), lsb-base (>= 1.3-9ubuntu3)
Filename: pool/main/i/initrd-tools/initrd-tools_0.1.78ubuntu2_all.deb
Size: 30988
MD5sum: d8cacbf0c12ccae9e47b29ac3b9a5e0d
Description: tools to create initrd image for prepackaged Linux kernel
 This package contains tools needed to generate an initrd image suitable for
 booting a prepackaged Linux kernel image (as shipped with the Debian main
 distribution).  It does not cater for other uses of initrd at the moment.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

---

### Post by carlosqueso on 2005-12-14
which would explain why I can't make a kernel with --initrd :-D  thanks guys!

---

