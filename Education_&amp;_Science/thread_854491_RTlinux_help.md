---
title: "RTlinux help"
date: 2008-07-09
forum: Education &amp; Science
---

### Post by Maccabee on 2008-07-09
Im running a Ubuntu hardy with linux kernel 2.6.24,
I want to install rtlinux on it ([www.rtlinuxfree.com](www.rtlinuxfree.com))
The package has only patches upto 2.6.9 kernel , i downloaded 2.6.9 applied the patch
tried to compile in the debian way im getting stuck

at this stage
Code:
 fakeroot make-kpkg --initrd --append-to-version=-some-string-here kernel-image kernel-headers


The error is
Code:
include/linux/skbuff.h:1017: warning: pointer targets in passing argument 2 of &#8216;csum_and_copy_from_user&#8217; differ in signedness
  CC      init/do_mounts_rd.o
In file included from include/asm/mpspec.h:5,
                 from include/asm/smp.h:18,
                 from include/linux/smp.h:17,
                 from include/linux/topology.h:33,
                 from include/linux/mmzone.h:371,
                 from include/linux/gfp.h:4,
                 from include/linux/slab.h:15,
                 from include/linux/percpu.h:4,
                 from include/linux/rcupdate.h:41,
                 from include/linux/dcache.h:10,
                 from include/linux/fs.h:16,
                 from init/do_mounts_rd.c:3:
include/asm/mpspec_def.h:78: warning: &#8216;packed&#8217; attribute ignored for field of type &#8216;unsigned char[6]&#8217;
init/do_mounts_rd.c: In function &#8216;identify_ramdisk_image&#8217;:
init/do_mounts_rd.c:73: warning: pointer targets in passing argument 2 of &#8216;sys_read&#8217; differ in signedness
init/do_mounts_rd.c:108: warning: pointer targets in passing argument 2 of &#8216;sys_read&#8217; differ in signedness
init/do_mounts_rd.c: In function &#8216;fill_inbuf&#8217;:
init/do_mounts_rd.c:351: warning: pointer targets in passing argument 2 of &#8216;sys_read&#8217; differ in signedness
init/do_mounts_rd.c: In function &#8216;flush_window&#8217;:
init/do_mounts_rd.c:372: warning: pointer targets in passing argument 2 of &#8216;sys_write&#8217; differ in signedness
  CC      init/do_mounts_initrd.o
In file included from include/asm/mpspec.h:5,
                 from include/asm/smp.h:18,
                 from include/linux/smp.h:17,
                 from include/linux/topology.h:33,
                 from include/linux/mmzone.h:371,
                 from include/linux/gfp.h:4,
                 from include/linux/slab.h:15,
                 from include/linux/percpu.h:4,
                 from include/linux/rcupdate.h:41,
                 from include/linux/dcache.h:10,
                 from include/linux/fs.h:16,
                 from init/do_mounts_initrd.c:4:
include/asm/mpspec_def.h:78: warning: &#8216;packed&#8217; attribute ignored for field of type &#8216;unsigned char[6]&#8217;
  LD      init/mounts.o
  CC      init/initramfs.o
In file included from include/asm/mpspec.h:5,
                 from include/asm/smp.h:18,
                 from include/linux/smp.h:17,
                 from include/linux/topology.h:33,
                 from include/linux/mmzone.h:371,
                 from include/linux/gfp.h:4,
                 from include/linux/slab.h:15,
                 from include/linux/percpu.h:4,
                 from include/linux/rcupdate.h:41,
                 from include/linux/dcache.h:10,
                 from include/linux/fs.h:16,
                 from init/initramfs.c:2:
include/asm/mpspec_def.h:78: warning: &#8216;packed&#8217; attribute ignored for field of type &#8216;unsigned char[6]&#8217;
init/initramfs.c: In function &#8216;flush_window&#8217;:
init/initramfs.c:401: warning: pointer targets in passing argument 1 of &#8216;flush_buffer&#8217; differ in signedness
init/initramfs.c: In function &#8216;unpack_to_rootfs&#8217;:
init/initramfs.c:442: warning: pointer targets in assignment differ in signedness
  LD      init/built-in.o
  HOSTCC  usr/gen_init_cpio
  CPIO    usr/initramfs_data.cpio
  GZIP    usr/initramfs_data.cpio.gz
  AS      usr/initramfs_data.o
  LD      usr/built-in.o
  CC      arch/i386/kernel/process.o
In file included from include/asm/mpspec.h:5,
                 from include/asm/smp.h:18,
                 from include/linux/smp.h:17,
                 from include/linux/sched.h:23,
                 from arch/i386/kernel/process.c:17:
include/asm/mpspec_def.h:78: warning: &#8216;packed&#8217; attribute ignored for field of type &#8216;unsigned char[6]&#8217;
arch/i386/kernel/process.c: In function &#8216;show_regs&#8217;:
arch/i386/kernel/process.c:252: warning: pointer targets in passing argument 2 of &#8216;show_trace&#8217; differ in signedness
{standard input}: Assembler messages:
{standard input}:1394: Error: suffix or operands invalid for `mov'
{standard input}:1396: Error: suffix or operands invalid for `mov'
{standard input}:1743: Error: suffix or operands invalid for `mov'
{standard input}:1745: Error: suffix or operands invalid for `mov'
{standard input}:1856: Error: suffix or operands invalid for `mov'
{standard input}:1857: Error: suffix or operands invalid for `mov'
{standard input}:2031: Error: suffix or operands invalid for `mov'
{standard input}:2033: Error: suffix or operands invalid for `mov'
{standard input}:2150: Error: suffix or operands invalid for `mov'
{standard input}:2163: Error: suffix or operands invalid for `mov'
make[2]: *** [arch/i386/kernel/process.o] Error 1
make[1]: *** [arch/i386/kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.9'
make: *** [debian/stamp-build-kernel] Error 2



      I ve some basic questions

      1. Can i compile a linux kernel 2.6.9 in a 2.6.24 OS??
      2..If possible ,Can i boot with that kernel into my current OS
      3.If 1 not possible then wat is the most appropriate solution without changing my current OS??

---

### Post by bite on 2008-07-09
I cannot help you with rtlinux but I suggest you try [http://www.xenomai.org](http://www.xenomai.org)

Same functionalities. Well documented.

Last version 2.4.4 matches up to kernel 2.6.25

---

