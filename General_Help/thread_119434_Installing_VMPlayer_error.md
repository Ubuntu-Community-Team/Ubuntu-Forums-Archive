---
title: "Installing VMPlayer error"
date: 2006-01-19
forum: General Help
---

### Post by pjman on 2006-01-19
Hi,

When installing vmplayer and I run /usr/bin/vmware-config.pl  I get the following error:

```

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Player is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux-headers-2.6.12-10-686/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config8/vmmon-only'
make -C /usr/src/linux-headers-2.6.12-10-686/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-686'
  CC [M]  /tmp/vmware-config8/vmmon-only/linux/driver.o
In file included from include/linux/kernel.h:12,
                 from /tmp/vmware-config8/vmmon-only/linux/driver.c:11:
include/linux/stddef.h:1:1: unterminated comment
include/linux/stddef.h:12:5: warning: no newline at end of file
In file included from include/linux/kernel.h:13,
                 from /tmp/vmware-config8/vmmon-only/linux/driver.c:11:
include/linux/types.h:1: error: parse error before numeric constant
In file included from include/linux/kernel.h:13,
                 from /tmp/vmware-config8/vmmon-only/linux/driver.c:11:
include/linux/types.h:12:2: #endif without #if
include/linux/types.h:13:1: warning: null character(s) ignored
include/linux/types.h:13:3332: warning: no newline at end of file
In file included from include/linux/bitops.h:3,
                 from include/linux/kernel.h:15,
                 from /tmp/vmware-config8/vmmon-only/linux/driver.c:11:
include/asm/types.h:6: warning: return type defaults to `int'
include/asm/types.h:6: warning: function declaration isn't a prototype
include/asm/types.h: In function `ET':
include/asm/types.h:6: error: storage class specified for parameter `umode_t'

```

The list is actually much longer. I can post it if needed. I do have my Linux Headers installed for my version (2.6.12-10-686). Any ideas?

Thanks

---

