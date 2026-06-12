---
title: "unreal tournament 2004 EC, need help"
date: 2007-01-27
forum: Gaming &amp; Leisure
---

### Post by Neo Tom Bombadil on 2007-01-27
I run 64 bit edgy and am following this guide [http://utforums.epicgames.com/showthread.php?t=558146](http://utforums.epicgames.com/showthread.php?t=558146). can sombody explain how to modify unshield source so i dont get the "...MD5 checksum failure", its listed in the guide i just dont know what to do. I know how to follow the rest of the guide just not this one part.

---

### Post by Neo Tom Bombadil on 2007-01-27
more specificly [http://packages.debian.org/unstable/source/unshield](http://packages.debian.org/unstable/source/unshield) has the source code, I decompressed it, so where in the file do i add thouse lines of code? then how do i compile to make it work after im done that?

---

### Post by Neo Tom Bombadil on 2007-01-27
for example [http://ftp.debian.org/debian/pool/main/u/unshield/unshield_0.5-3.diff.gz](http://ftp.debian.org/debian/pool/main/u/unshield/unshield_0.5-3.diff.gz) needs to be modified like this "Decompress, patch to 0.5-3, and make the following changes:

For lib/md5/global.h
add:

#include <stdint.h>

change line 17
typedef unsigned short int UINT2;
to
typedef uint16_t UINT2;

change line 20
typedef unsigned long int UINT4;
to
typedef uint32_t UINT4;

in lib/md5/md5c.c, change line 71 from:
#define ROTATE_LEFT(x, n) (((x) << (n)) | ((x) >> (32-(n))))
to:
#define ROTATE_LEFT(x, n) ((((x) << (n)) & 0xffffffffU) | ((x) >> (32-(n))))


do ./configure, make.

Compiled it with gcc version 4.1.2 and it worked. "

iim slowly figuring it out.. so i may now need any help

---

