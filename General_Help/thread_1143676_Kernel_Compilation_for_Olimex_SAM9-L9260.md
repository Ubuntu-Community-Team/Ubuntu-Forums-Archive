---
title: "Kernel Compilation for Olimex SAM9-L9260"
date: 2009-04-30
forum: General Help
---

### Post by ermankoybasi on 2009-04-30
Hi! I have an Olimex sam9-l9260 board and I need to compile a custom kernel under Ubuntu 8.04 for the board to be able to run some codes. For this custom kernel I need to apply two patches sent by Olimex with the support CD. The first one is applied without problems which adds ARM board support to the kernel but when I try to apply the second patch which adds support for this specific Olimex board I get this:

erman@erman-laptop:~/linux-2.6.26.3$ bzcat sam9_l9260.diff.bz2 | patch -p1
The next patch would create the file arch/arm/configs/sam9_l9260_defconfig,
which already exists!  Assume -R? [n] y
patching file arch/arm/configs/sam9_l9260_defconfig
Hunk #1 FAILED at 1.
File arch/arm/configs/sam9_l9260_defconfig is not empty after patch, as expected
1 out of 1 hunk FAILED -- saving rejects to file arch/arm/configs/sam9_l9260_defconfig.rej
The next patch would create the file arch/arm/mach-at91/board-sam9-l9260.c,
which already exists!  Assume -R? [n] n
Apply anyway? [n] n
Skipping patch.

If this means that the patch is already applied then I have a problem with the following step which is "make xconfig" whose output can be seen here:

erman@erman-laptop:~/linux-2.6.26.3$ make xconfig
  HOSTCC  scripts/basic/fixdep
scripts/basic/fixdep.c:107:23: error: sys/types.h: No such file or directory
scripts/basic/fixdep.c:108:22: error: sys/stat.h: No such file or directory
scripts/basic/fixdep.c:109:22: error: sys/mman.h: No such file or directory
scripts/basic/fixdep.c:110:20: error: unistd.h: No such file or directory
scripts/basic/fixdep.c:111:19: error: fcntl.h: No such file or directory
scripts/basic/fixdep.c:112:20: error: string.h: No such file or directory
scripts/basic/fixdep.c:113:20: error: stdlib.h: No such file or directory
scripts/basic/fixdep.c:114:19: error: stdio.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.2.4/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.2.4/include/limits.h:11,
                 from scripts/basic/fixdep.c:115:
/usr/lib/gcc/i486-linux-gnu/4.2.4/include/limits.h:122:61: error: limits.h: No such file or directory
And this goes on like this. Anyone got an idea? Thanks in advance.

---

