---
title: "APT archive - where I can find metapackage information ?"
date: 2009-06-18
forum: General Help
---

### Post by ActiveFrost on 2009-06-18
```
/var/cache/apt/archives/
```
I see only .deb files and empty partial folder. Where I can find metapackage information ? For example, if I've downlodaed ubuntu-restricted-extras, flash-plugin/unrar/etc. are all in separate .deb files. How I can find out, which package belongs to what ? Keep in mind, "go and find it Online" will not work - I need an offline solution ( creating a small application for myself and who knows .. maybe for someone else ).

---

### Post by dcstar on 2009-06-18
> **ActiveFrost said:**
> ```
/var/cache/apt/archives/
```
I see only .deb files and empty partial folder. Where I can find metapackage information ? For example, if I've downlodaed ubuntu-restricted-extras, flash-plugin/unrar/etc. are all in separate .deb files. How I can find out, which package belongs to what ? Keep in mind, "go and find it Online" will not work - I need an offline solution ( creating a small application for myself and who knows .. maybe for someone else ).

AFAIK the repository itself contains this info, not the .deb files.

---

### Post by ActiveFrost on 2009-06-18
So, it's impossible to get this info in offline mode ?

---

### Post by Lampi on 2009-06-18
> **ActiveFrost said:**
> So, it's impossible to get this info in offline mode ?
You can use apt-cache show <nameofyourpackage>

for example:

```

~$ apt-cache show grub
Package: grub
Priority: optional
Section: admin
Installed-Size: 924
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Original-Maintainer: Grub Maintainers <pkg-grub-devel@lists.alioth.debian.org>
Architecture: i386
Version: 0.97-29ubuntu53
Provides: linux-boot-loader
Depends: libc6 (>= 2.4), libncurses5 (>= 5.6+20071006-3), grub-common, udev (>= 117-5), ucf (>= 3.004-0ubuntu2), debconf (>= 1.5.19) | cdebconf
Suggests: grub-doc, mdadm
Filename: pool/main/g/grub/grub_0.97-29ubuntu53_i386.deb
Size: 404142
MD5sum: ee71b617605d0e30f2ba2b35dd02cf77
SHA1: b7b327f6ee3d52353bd29e72cf8971e972b0acd4
SHA256: b2b8d7e380468d5a2dd35a758181359602ae117cab7d7ee04635eed8ccb138c7
Description: GRand Unified Bootloader
 GRUB is a GPLed bootloader intended to unify bootloading across x86
 operating systems.  In addition to loading the Linux kernel,
 it implements the Multiboot standard, which allows for flexible loading
 of multiple boot images (needed for modular kernels such as the GNU Hurd).
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Task: ubuntu-live, kubuntu-live, edubuntu-live, xubuntu-live, mobile-live, mobile-mid, mythbuntu-live
```
This browses your package database offline

---

### Post by ActiveFrost on 2009-06-18
> **Lampi said:**
> You can use apt-cache show <nameofyourpackage>
Perfect ! Thanks a lot :)

---

