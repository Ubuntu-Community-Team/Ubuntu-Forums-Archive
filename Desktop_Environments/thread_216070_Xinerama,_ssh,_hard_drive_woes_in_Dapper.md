---
title: "Xinerama, ssh, hard drive woes in Dapper"
date: 2006-07-14
forum: Desktop Environments
---

### Post by HeyItry on 2006-07-14
I've upgraded to Dapper on three machines, each of which made it to a bootable state without a hitch, but my Xinerama machine, also my Mythbackend, is having some trouble.  The cards are one intel integrated video card, and two s3virge cards -- Diamond Stealth 3D 2000, to be exact, and using the s3virge I get the following errors in my Xorg.0.log:

```
(**) S3VIRGE(1): Depth 16, (--) framebuffer bpp 16
(==) S3VIRGE(1): RGB weight 565
(==) S3VIRGE(1): Default visual is TrueColor
(**) S3VIRGE(1): Option "UseFB"
(==) S3VIRGE(1): Using HW Cursor
(==) S3VIRGE(1): Using fb.
(**) S3VIRGE(1): UseFB option is deprecated.
(==) S3VIRGE(1): mx_cr3a_fix.
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules/libvbe.so
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) S3VIRGE(1): initializing int10
Requesting insufficient memory window!: start: 0xfc000000 end: 0xfc0fffff size 0xfc020000
Requesting insufficient memory window!: start: 0xec100000 end: 0xf7ffffff size 0xfc020000
Requesting insufficient memory window!: start: 0xfc000000 end: 0xfc0fffff size 0xfc020000
Requesting insufficient memory window!: start: 0xec100000 end: 0xf7ffffff size 0xfc020000
Requesting insufficient memory window!: start: 0xfc000000 end: 0xfc0fffff size 0xfc020000
Requesting insufficient memory window!: start: 0xec100000 end: 0xf7ffffff size 0xfc020000
(EE) S3VIRGE(1): Cannot read V_BIOS
(--) S3VIRGE(1): Chipset: "virge"
(==) S3VIRGE(1): XVideo not supported.
(II) S3VIRGE(1): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) S3VIRGE(1): vgaHWGetIOBase: hwp->IOBase is 0x03b0, hwp->PIOOffset is 0x0000

```

Also, it takes several minutes before I can log in via ssh and my hard drive is constantly being accessed on both desktops.  I believe the latter is interfering with my recordings, so any help on that is appreciated.  Other than that, I'm loving using Dapper on my machines and am even recommending it to friends when I fix theirs.

---

