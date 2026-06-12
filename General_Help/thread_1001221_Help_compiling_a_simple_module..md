---
title: "Help compiling a simple module."
date: 2008-12-03
forum: General Help
---

### Post by zilla62 on 2008-12-03
I'm trying to compile this simple module from Alessandro Rubini's Linux Device Driver book via the command

> gcc -c -I/usr/src/linux-headers-2.6.27-9-generic/include hello.c

#define MODULE
#include <linux/module.h>

int init_module(void)
{ 
   printk("<1>Hello world\n"); return 0;
}

void cleanup_module(void)
{ 
   printk("<1>Goodbye world\n");
}

...and get these. I'm rusty so why?

In file included from /usr/src/linux-headers-2.6.27-9-generic/include/asm/processor.h:15,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/prefetch.h:14,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/list.h:6,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:9,
                 from hello.c:2:
/usr/src/linux-headers-2.6.27-9-generic/include/asm/current.h:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘struct’
In file included from /usr/src/linux-headers-2.6.27-9-generic/include/asm/cmpxchg_64.h:4,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/asm/cmpxchg.h:4,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/asm/system.h:7,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/asm/processor.h:17,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/prefetch.h:14,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/list.h:6,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:9,
                 from hello.c:2:
/usr/src/linux-headers-2.6.27-9-generic/include/asm/alternative.h:45: error: expected specifier-qualifier-list before ‘u8’
In file included from /usr/src/linux-headers-2.6.27-9-generic/include/asm/processor.h:21,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/prefetch.h:14,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/list.h:6,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:9,
                 from hello.c:2:
/usr/src/linux-headers-2.6.27-9-generic/include/asm/desc_defs.h:29: error: expected specifier-qualifier-list before ‘u16’
/usr/src/linux-headers-2.6.27-9-generic/include/asm/desc_defs.h:46: error: expected specifier-qualifier-list before ‘u16’
/usr/src/linux-headers-2.6.27-9-generic/include/asm/desc_defs.h:66: error: expected specifier-qualifier-list before ‘u16’
In file included from /usr/src/linux-headers-2.6.27-9-generic/include/linux/bitops.h:17,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/bitmap.h:7,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:139,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/asm/processor.h:25,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/prefetch.h:14,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/list.h:6,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:9,
                 from hello.c:2:
/usr/src/linux-headers-2.6.27-9-generic/include/asm/bitops.h: In function ‘set_bit’:
/usr/src/linux-headers-2.6.27-9-generic/include/asm/bitops.h:61: error: ‘u8’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.27-9-generic/include/asm/bitops.h:61: error: (Each undeclared identifier is reported only once
/usr/src/linux-headers-2.6.27-9-generic/include/asm/bitops.h:61: error: for each function it appears in.)
/usr/src/linux-headers-2.6.27-9-generic/include/asm/bitops.h: In function ‘clear_bit’:
/usr/src/linux-headers-2.6.27-9-generic/include/asm/bitops.h:98: error: ‘u8’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.27-9-generic/include/asm/bitops.h:98: error: expected ‘)’ before ‘~’ token
/usr/src/linux-headers-2.6.27-9-generic/include/asm/bitops.h: In function ‘constant_test_bit’:
/usr/src/linux-headers-2.6.27-9-generic/include/asm/bitops.h:297: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
In file included from /usr/src/linux-headers-2.6.27-9-generic/include/asm/bitops.h:447,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/bitops.h:17,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/bitmap.h:7,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:139,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/asm/processor.h:25,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/prefetch.h:14,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/list.h:6,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:9,
                 from hello.c:2:
/usr/src/linux-headers-2.6.27-9-generic/include/asm-generic/bitops/fls64.h:33:2: error: #error BITS_PER_LONG not 32 or 64
In file included from /usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:139,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/asm/processor.h:25,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/prefetch.h:14,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/list.h:6,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:9,
                 from hello.c:2:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/bitmap.h: In function ‘bitmap_zero’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/bitmap.h:142: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.27-9-generic/include/linux/bitmap.h: In function ‘bitmap_fill’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/bitmap.h:157: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.27-9-generic/include/linux/bitmap.h: In function ‘bitmap_copy’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/bitmap.h:163: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.27-9-generic/include/linux/bitmap.h: In function ‘bitmap_and’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/bitmap.h:174: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.27-9-generic/include/linux/bitmap.h: In function ‘bitmap_or’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/bitmap.h:183: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.27-9-generic/include/linux/bitmap.h: In function ‘bitmap_xor’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/bitmap.h:192: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.27-9-generic/include/linux/bitmap.h: In function ‘bitmap_andnot’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/bitmap.h:201: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.27-9-generic/include/linux/bitmap.h: In function ‘bitmap_complement’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/bitmap.h:210: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.27-9-generic/include/linux/bitmap.h: In function ‘bitmap_equal’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/bitmap.h:219: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.27-9-generic/include/linux/bitmap.h: In function ‘bitmap_intersects’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/bitmap.h:228: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.27-9-generic/include/linux/bitmap.h: In function ‘bitmap_subset’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/bitmap.h:237: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.27-9-generic/include/linux/bitmap.h: In function ‘bitmap_empty’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/bitmap.h:245: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.27-9-generic/include/linux/bitmap.h: In function ‘bitmap_full’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/bitmap.h:253: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.27-9-generic/include/linux/bitmap.h: In function ‘bitmap_weight’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/bitmap.h:261: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.27-9-generic/include/linux/bitmap.h: In function ‘bitmap_shift_right’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/bitmap.h:269: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.27-9-generic/include/linux/bitmap.h: In function ‘bitmap_shift_left’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/bitmap.h:278: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
In file included from /usr/src/linux-headers-2.6.27-9-generic/include/asm/processor.h:25,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/prefetch.h:14,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/list.h:6,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:9,
                 from hello.c:2:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h: At top level:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:141: error: expected specifier-qualifier-list before ‘DECLARE_BITMAP’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h: In function ‘__cpu_set’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:147: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h: In function ‘__cpu_clear’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:153: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h: In function ‘__cpus_setall’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:159: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h: In function ‘__cpus_clear’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:165: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h: In function ‘__cpu_test_and_set’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:174: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h: In function ‘__cpus_and’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:181: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:181: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:181: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h: In function ‘__cpus_or’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:188: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:188: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:188: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h: In function ‘__cpus_xor’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:195: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:195: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:195: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h: In function ‘__cpus_andnot’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:203: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:203: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:203: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h: In function ‘__cpus_complement’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:210: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:210: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h: In function ‘__cpus_equal’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:217: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:217: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h: In function ‘__cpus_intersects’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:224: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:224: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h: In function ‘__cpus_subset’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:231: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:231: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h: In function ‘__cpus_empty’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:237: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h: In function ‘__cpus_full’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:243: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h: In function ‘__cpus_weight’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:249: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h: In function ‘__cpus_shift_right’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:257: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:257: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h: In function ‘__cpus_shift_left’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:265: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:265: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h: At top level:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:276: error: ‘BITS_PER_LONG’ undeclared here (not in a function)
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:276: error: variably modified ‘cpu_bit_bitmap’ at file scope
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h: In function ‘__cpumask_scnprintf’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:344: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h: In function ‘__cpumask_parse_user’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:352: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h: In function ‘__cpulist_scnprintf’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:360: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h: In function ‘__cpulist_parse’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:366: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h: In function ‘__cpu_remap’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:374: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:374: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h: In function ‘__cpus_remap’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:382: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:382: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:382: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:382: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h: In function ‘__cpus_onto’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:390: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:390: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:390: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h: In function ‘__cpus_fold’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:398: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cpumask.h:398: error: ‘cpumask_t’ has no member named ‘bits’
In file included from /usr/src/linux-headers-2.6.27-9-generic/include/linux/prefetch.h:14,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/list.h:6,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:9,
                 from hello.c:2:
/usr/src/linux-headers-2.6.27-9-generic/include/asm/processor.h: At top level:
/usr/src/linux-headers-2.6.27-9-generic/include/asm/processor.h:98: error: expected specifier-qualifier-list before ‘u16’
/usr/src/linux-headers-2.6.27-9-generic/include/asm/processor.h:112: error: ‘CONFIG_X86_L1_CACHE_SHIFT’ undeclared here (not in a function)
/usr/src/linux-headers-2.6.27-9-generic/include/asm/processor.h:112: error: requested alignment is not a constant
In file included from /usr/src/linux-headers-2.6.27-9-generic/include/linux/prefetch.h:14,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/list.h:6,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:9,
                 from hello.c:2:
/usr/src/linux-headers-2.6.27-9-generic/include/asm/processor.h:152:1: warning: "cache_line_size" redefined
In file included from /usr/src/linux-headers-2.6.27-9-generic/include/asm/pda.h:7,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/asm/current.h:19,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/asm/processor.h:15,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/prefetch.h:14,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/list.h:6,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:9,
                 from hello.c:2:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/cache.h:64:1: warning: this is the location of the previous definition
/usr/src/linux-headers-2.6.27-9-generic/include/asm/processor.h:182: error: expected ‘)’ before ‘*’ token
/usr/src/linux-headers-2.6.27-9-generic/include/asm/processor.h:222: error: expected specifier-qualifier-list before ‘u32’
/usr/src/linux-headers-2.6.27-9-generic/include/asm/processor.h:233: error: requested alignment is not a constant
/usr/src/linux-headers-2.6.27-9-generic/include/asm/processor.h:270: error: requested alignment is not a constant
/usr/src/linux-headers-2.6.27-9-generic/include/asm/processor.h:284: error: expected specifier-qualifier-list before ‘u32’
/usr/src/linux-headers-2.6.27-9-generic/include/asm/processor.h:300: error: expected specifier-qualifier-list before ‘u16’
/usr/src/linux-headers-2.6.27-9-generic/include/asm/processor.h:330: error: expected specifier-qualifier-list before ‘u32’
/usr/src/linux-headers-2.6.27-9-generic/include/asm/processor.h: In function ‘native_load_sp0’:
/usr/src/linux-headers-2.6.27-9-generic/include/asm/processor.h:496: error: ‘struct x86_hw_tss’ has no member named ‘sp0’
/usr/src/linux-headers-2.6.27-9-generic/include/asm/processor.h: In function ‘wbinvd_halt’:
/usr/src/linux-headers-2.6.27-9-generic/include/asm/processor.h:747: error: ‘cpu_has_clflush’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.27-9-generic/include/asm/processor.h: At top level:
/usr/src/linux-headers-2.6.27-9-generic/include/asm/processor.h:929: warning: ‘struct pt_regs’ declared inside parameter list
/usr/src/linux-headers-2.6.27-9-generic/include/asm/processor.h:929: warning: its scope is only this definition or declaration, which is probably not what you want
In file included from /usr/src/linux-headers-2.6.27-9-generic/include/linux/preempt.h:9,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/spinlock.h:50,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/mmzone.h:7,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/gfp.h:4,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/kmod.h:22,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:13,
                 from hello.c:2:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/thread_info.h:26: error: expected specifier-qualifier-list before ‘u32’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/thread_info.h:39: error: expected specifier-qualifier-list before ‘u64’
In file included from /usr/src/linux-headers-2.6.27-9-generic/include/linux/thread_info.h:47,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/preempt.h:9,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/spinlock.h:50,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/mmzone.h:7,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/gfp.h:4,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/kmod.h:22,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:13,
                 from hello.c:2:
/usr/src/linux-headers-2.6.27-9-generic/include/asm/thread_info.h: In function ‘current_thread_info’:
/usr/src/linux-headers-2.6.27-9-generic/include/asm/thread_info.h:206: error: expected expression before ‘struct’
/usr/src/linux-headers-2.6.27-9-generic/include/asm/thread_info.h:206: error: expected expression before ‘struct’
/usr/src/linux-headers-2.6.27-9-generic/include/asm/thread_info.h:206: error: expected expression before ‘struct’
/usr/src/linux-headers-2.6.27-9-generic/include/asm/thread_info.h:206: error: ‘THREAD_SIZE’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.27-9-generic/include/asm/thread_info.h: In function ‘stack_thread_info’:
/usr/src/linux-headers-2.6.27-9-generic/include/asm/thread_info.h:214: error: ‘THREAD_SIZE’ undeclared (first use in this function)
In file included from /usr/src/linux-headers-2.6.27-9-generic/include/linux/mmzone.h:16,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/gfp.h:4,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/kmod.h:22,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:13,
                 from hello.c:2:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h: At top level:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:92: error: expected specifier-qualifier-list before ‘DECLARE_BITMAP’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h: In function ‘__node_set’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:98: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h: In function ‘__node_clear’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:104: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h: In function ‘__nodes_setall’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:110: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h: In function ‘__nodes_clear’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:116: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h: In function ‘__node_test_and_set’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:126: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h: In function ‘__nodes_and’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:134: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:134: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:134: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h: In function ‘__nodes_or’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:142: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:142: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:142: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h: In function ‘__nodes_xor’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:150: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:150: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:150: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h: In function ‘__nodes_andnot’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:158: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:158: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:158: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h: In function ‘__nodes_complement’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:166: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:166: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h: In function ‘__nodes_equal’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:174: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:174: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h: In function ‘__nodes_intersects’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:182: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:182: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h: In function ‘__nodes_subset’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:190: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:190: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h: In function ‘__nodes_empty’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:196: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h: In function ‘__nodes_full’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:202: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h: In function ‘__nodes_weight’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:208: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h: In function ‘__nodes_shift_right’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:216: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:216: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h: In function ‘__nodes_shift_left’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:224: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:224: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h: In function ‘__first_node’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:233: error: expected expression before ‘int’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h: In function ‘__next_node’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:239: error: expected expression before ‘int’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h: In function ‘__first_unset_node’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:257: error: expected expression before ‘int’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h: In function ‘__nodemask_scnprintf’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:292: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h: In function ‘__nodemask_parse_user’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:300: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h: In function ‘__nodelist_scnprintf’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:308: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h: In function ‘__nodelist_parse’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:314: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h: In function ‘__node_remap’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:322: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:322: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h: In function ‘__nodes_remap’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:330: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:330: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:330: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:330: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h: In function ‘__nodes_onto’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:338: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:338: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:338: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h: In function ‘__nodes_fold’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:346: error: ‘nodemask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/nodemask.h:346: error: ‘nodemask_t’ has no member named ‘bits’
In file included from /usr/src/linux-headers-2.6.27-9-generic/include/linux/gfp.h:4,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/kmod.h:22,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:13,
                 from hello.c:2:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/mmzone.h: At top level:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/mmzone.h:307: error: expected specifier-qualifier-list before ‘wait_queue_head_t’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/mmzone.h:546: error: expected specifier-qualifier-list before ‘wait_queue_head_t’
In file included from /usr/src/linux-headers-2.6.27-9-generic/include/linux/notifier.h:13,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/memory_hotplug.h:6,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/mmzone.h:560,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/gfp.h:4,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/kmod.h:22,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:13,
                 from hello.c:2:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/mutex.h:136: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘mutex_lock_interruptible’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/mutex.h:137: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘mutex_lock_killable’
In file included from /usr/src/linux-headers-2.6.27-9-generic/include/linux/memory_hotplug.h:6,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/mmzone.h:560,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/gfp.h:4,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/kmod.h:22,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:13,
                 from hello.c:2:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/notifier.h:62: error: field ‘rwsem’ has incomplete type
In file included from /usr/src/linux-headers-2.6.27-9-generic/include/linux/mmzone.h:560,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/gfp.h:4,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/kmod.h:22,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:13,
                 from hello.c:2:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/memory_hotplug.h: In function ‘mhp_notimplemented’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/memory_hotplug.h:183: error: ‘KERN_WARNING’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.27-9-generic/include/linux/memory_hotplug.h:183: error: expected ‘)’ before string constant
/usr/src/linux-headers-2.6.27-9-generic/include/linux/memory_hotplug.h: At top level:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/memory_hotplug.h:214: error: expected declaration specifiers or ‘...’ before ‘u64’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/memory_hotplug.h:214: error: expected declaration specifiers or ‘...’ before ‘u64’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/memory_hotplug.h:215: error: expected declaration specifiers or ‘...’ before ‘u64’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/memory_hotplug.h:215: error: expected declaration specifiers or ‘...’ before ‘u64’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/memory_hotplug.h:216: error: expected ‘)’ before ‘start’
In file included from /usr/src/linux-headers-2.6.27-9-generic/include/linux/gfp.h:4,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/kmod.h:22,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:13,
                 from hello.c:2:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/mmzone.h: In function ‘populated_zone’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/mmzone.h:593: error: ‘struct zone’ has no member named ‘present_pages’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/mmzone.h: In function ‘is_normal’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/mmzone.h:642: error: ‘struct zone’ has no member named ‘zone_pgdat’
In file included from /usr/src/linux-headers-2.6.27-9-generic/include/linux/topology.h:34,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/mmzone.h:683,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/gfp.h:4,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/kmod.h:22,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:13,
                 from hello.c:2:
/usr/src/linux-headers-2.6.27-9-generic/include/asm/topology.h: At top level:
/usr/src/linux-headers-2.6.27-9-generic/include/asm/topology.h:233: error: expected declaration specifiers or ‘...’ before ‘u32’
In file included from /usr/src/linux-headers-2.6.27-9-generic/include/linux/kmod.h:22,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:13,
                 from hello.c:2:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/gfp.h:108: error: expected ‘)’ before ‘gfp_flags’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/gfp.h:120: error: expected ‘)’ before ‘flags’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/gfp.h:147: error: expected ‘)’ before ‘flags’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/gfp.h:164: error: expected declaration specifiers or ‘...’ before ‘gfp_t’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/gfp.h: In function ‘node_zonelist’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/gfp.h:166: error: ‘flags’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.27-9-generic/include/linux/gfp.h: At top level:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/gfp.h:177: error: expected ‘)’ before ‘gfp_mask’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/gfp.h:181: error: expected ‘)’ before ‘gfp_mask’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/gfp.h:188: error: expected ‘)’ before ‘gfp_mask’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/gfp.h:195: error: expected declaration specifiers or ‘...’ before ‘gfp_t’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/gfp.h: In function ‘alloc_pages_node’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/gfp.h:205: error: ‘gfp_mask’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.27-9-generic/include/linux/gfp.h:205: error: too many arguments to function ‘node_zonelist’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/gfp.h:205: warning: return makes pointer from integer without a cast
/usr/src/linux-headers-2.6.27-9-generic/include/linux/gfp.h: At top level:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/gfp.h:228: error: expected ‘)’ before ‘gfp_mask’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/gfp.h:229: error: expected ‘)’ before ‘gfp_mask’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/gfp.h:231: error: expected declaration specifiers or ‘...’ before ‘gfp_t’
In file included from /usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:13,
                 from hello.c:2:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/kmod.h:46: error: expected declaration specifiers or ‘...’ before ‘gfp_t’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/kmod.h: In function ‘call_usermodehelper’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/kmod.h:73: error: ‘gfp_t’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.27-9-generic/include/linux/kmod.h:73: error: expected ‘;’ before ‘gfp_mask’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/kmod.h:75: error: ‘gfp_mask’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.27-9-generic/include/linux/kmod.h:75: error: too many arguments to function ‘call_usermodehelper_setup’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/kmod.h: In function ‘call_usermodehelper_keys’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/kmod.h:86: error: ‘gfp_t’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.27-9-generic/include/linux/kmod.h:86: error: expected ‘;’ before ‘gfp_mask’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/kmod.h:88: error: ‘gfp_mask’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.27-9-generic/include/linux/kmod.h:88: error: too many arguments to function ‘call_usermodehelper_setup’
In file included from /usr/src/linux-headers-2.6.27-9-generic/include/linux/kobject.h:21,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:16,
                 from hello.c:2:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/sysfs.h: At top level:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/sysfs.h:229: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘sysfs_init’
In file included from /usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:16,
                 from hello.c:2:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/kobject.h:37: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘uevent_seqnum’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/kobject.h:82: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘kobject_add’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/kobject.h:85: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘kobject_init_and_add’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/kobject.h:92: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘kobject_create’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/kobject.h:93: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘kobject_create_and_add’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/kobject.h:96: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘kobject_rename’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/kobject.h:97: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘kobject_move’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/kobject.h:102: error: expected declaration specifiers or ‘...’ before ‘gfp_t’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/kobject.h:159: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘kset_register’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/kobject.h:161: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘kset_create_and_add’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/kobject.h: In function ‘to_kset’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/kobject.h:167: error: expected expression before ‘struct’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/kobject.h:167: warning: pointer/integer type mismatch in conditional expression
In file included from /usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:18,
                 from hello.c:2:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/marker.h: At top level:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/marker.h:33: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/marker.h:125: error: expected declaration specifiers or ‘...’ before numeric constant
/usr/src/linux-headers-2.6.27-9-generic/include/linux/marker.h:125: error: expected declaration specifiers or ‘...’ before numeric constant
/usr/src/linux-headers-2.6.27-9-generic/include/linux/marker.h: In function ‘__printf’:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/marker.h:125: error: expected declaration specifiers before ‘___mark_check_format’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/marker.h:135: error: storage class specified for parameter ‘__mark_empty_function’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/marker.h:138: error: storage class specified for parameter ‘marker_probe_cb’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/marker.h:140: error: storage class specified for parameter ‘marker_probe_cb_noarg’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/marker.h:147: error: storage class specified for parameter ‘marker_probe_register’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/marker.h:153: error: storage class specified for parameter ‘marker_probe_unregister’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/marker.h:158: error: storage class specified for parameter ‘marker_probe_unregister_private_data’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/marker.h:161: error: storage class specified for parameter ‘marker_get_private_data’
In file included from /usr/src/linux-headers-2.6.27-9-generic/include/linux/percpu.h:5,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/asm/local.h:4,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:19,
                 from hello.c:2:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab.h:56: error: section attribute not allowed for ‘kmem_cache_init’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab.h:99: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__krealloc’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab.h:100: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘krealloc’
In file included from /usr/src/linux-headers-2.6.27-9-generic/include/linux/slab.h:128,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/percpu.h:5,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/asm/local.h:4,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:19,
                 from hello.c:2:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab_def.h:19: warning: empty declaration
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab_def.h:26: error: storage class specified for parameter ‘malloc_sizes’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab_def.h:28: error: expected declaration specifiers or ‘...’ before ‘gfp_t’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab_def.h:29: error: expected declaration specifiers or ‘...’ before ‘gfp_t’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab_def.h:31: error: expected declaration specifiers or ‘...’ before ‘gfp_t’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab_def.h:32: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
In file included from /usr/src/linux-headers-2.6.27-9-generic/include/linux/percpu.h:5,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/asm/local.h:4,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:19,
                 from hello.c:2:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab.h:182: error: expected declaration specifiers or ‘...’ before ‘gfp_t’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab.h:183: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab.h:200: error: expected declaration specifiers or ‘...’ before ‘gfp_t’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab.h:201: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab.h:205: error: expected declaration specifiers or ‘...’ before ‘gfp_t’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab.h:206: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab.h:210: error: expected declaration specifiers or ‘...’ before ‘gfp_t’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab.h:210: error: redefinition of parameter ‘kmem_cache_alloc’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab_def.h:28: error: previous definition of ‘kmem_cache_alloc’ was here
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab.h:213: error: expected declaration specifiers or ‘...’ before ‘gfp_t’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab.h:214: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab.h:265: error: expected declaration specifiers or ‘...’ before ‘gfp_t’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab.h:266: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab.h:275: error: expected declaration specifiers or ‘...’ before ‘gfp_t’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab.h:276: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab.h:286: error: expected declaration specifiers or ‘...’ before ‘gfp_t’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab.h:287: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
In file included from /usr/src/linux-headers-2.6.27-9-generic/include/asm/local.h:4,
                 from /usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:19,
                 from hello.c:2:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/percpu.h:84: error: expected declaration specifiers or ‘...’ before ‘gfp_t’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/percpu.h:85: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.27-9-generic/include/linux/percpu.h:90: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
In file included from /usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:19,
                 from hello.c:2:
/usr/src/linux-headers-2.6.27-9-generic/include/asm/local.h:12: error: storage class specified for parameter ‘local_t’
/usr/src/linux-headers-2.6.27-9-generic/include/asm/local.h:19: error: expected ‘)’ before ‘*’ token
/usr/src/linux-headers-2.6.27-9-generic/include/asm/local.h:25: error: expected ‘)’ before ‘*’ token
/usr/src/linux-headers-2.6.27-9-generic/include/asm/local.h:31: error: expected declaration specifiers or ‘...’ before ‘local_t’
/usr/src/linux-headers-2.6.27-9-generic/include/asm/local.h:32: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.27-9-generic/include/asm/local.h:38: error: expected declaration specifiers or ‘...’ before ‘local_t’
/usr/src/linux-headers-2.6.27-9-generic/include/asm/local.h:39: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.27-9-generic/include/asm/local.h:54: error: expected declaration specifiers or ‘...’ before ‘local_t’
/usr/src/linux-headers-2.6.27-9-generic/include/asm/local.h:55: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.27-9-generic/include/asm/local.h:72: error: expected ‘)’ before ‘*’ token
/usr/src/linux-headers-2.6.27-9-generic/include/asm/local.h:90: error: expected ‘)’ before ‘*’ token
/usr/src/linux-headers-2.6.27-9-generic/include/asm/local.h:109: error: expected declaration specifiers or ‘...’ before ‘local_t’
/usr/src/linux-headers-2.6.27-9-generic/include/asm/local.h:110: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.27-9-generic/include/asm/local.h:126: error: expected declaration specifiers or ‘...’ before ‘local_t’
/usr/src/linux-headers-2.6.27-9-generic/include/asm/local.h:127: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.27-9-generic/include/asm/local.h:151: error: expected declaration specifiers or ‘...’ before ‘local_t’
/usr/src/linux-headers-2.6.27-9-generic/include/asm/local.h:152: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
In file included from /usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:21,
                 from hello.c:2:
/usr/src/linux-headers-2.6.27-9-generic/include/asm/module.h:5: warning: empty declaration
In file included from /usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:21,
                 from hello.c:2:
/usr/src/linux-headers-2.6.27-9-generic/include/asm/module.h:70:2: error: #error unknown processor family
In file included from hello.c:2:
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:33: warning: empty declaration
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:39: warning: empty declaration
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:45: warning: empty declaration
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:47: warning: empty declaration
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:57: warning: empty declaration
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:65: error: storage class specified for parameter ‘init_module’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:66: error: storage class specified for parameter ‘cleanup_module’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:69: warning: empty declaration
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:84: error: storage class specified for parameter ‘__this_module’
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:165: warning: empty declaration
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:467: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:473: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:479: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:484: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:494: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:498: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:503: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:514: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:519: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:524: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:531: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:536: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:541: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:547: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:554: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:558: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:563: warning: empty declaration
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:581: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:588: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:593: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:598: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
hello.c:5: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
hello.c:10: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:163: error: declaration for parameter ‘search_exception_tables’ but no such parameter
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:84: error: parameter ‘__this_module’ has incomplete type
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:84: error: declaration for parameter ‘__this_module’ but no such parameter
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:77: error: declaration for parameter ‘sort_main_extable’ but no such parameter
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:75: error: declaration for parameter ‘sort_extable’ but no such parameter
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:72: error: declaration for parameter ‘search_extable’ but no such parameter
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:66: error: declaration for parameter ‘cleanup_module’ but no such parameter
/usr/src/linux-headers-2.6.27-9-generic/include/linux/module.h:65: error: declaration for parameter ‘init_module’ but no such parameter
/usr/src/linux-headers-2.6.27-9-generic/include/asm/local.h:12: error: declaration for parameter ‘local_t’ but no such parameter
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab.h:210: error: declaration for parameter ‘kmem_cache_alloc’ but no such parameter
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab_def.h:29: error: declaration for parameter ‘__kmalloc’ but no such parameter
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab_def.h:28: error: declaration for parameter ‘kmem_cache_alloc’ but no such parameter
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab_def.h:26: error: declaration for parameter ‘malloc_sizes’ but no such parameter
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab.h:102: error: declaration for parameter ‘ksize’ but no such parameter
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab.h:101: error: declaration for parameter ‘kfree’ but no such parameter
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab.h:67: error: declaration for parameter ‘kmem_ptr_validate’ but no such parameter
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab.h:66: error: declaration for parameter ‘kmem_cache_name’ but no such parameter
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab.h:65: error: declaration for parameter ‘kmem_cache_size’ but no such parameter
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab.h:64: error: declaration for parameter ‘kmem_cache_free’ but no such parameter
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab.h:63: error: declaration for parameter ‘kmem_cache_shrink’ but no such parameter
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab.h:62: error: declaration for parameter ‘kmem_cache_destroy’ but no such parameter
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab.h:59: error: declaration for parameter ‘kmem_cache_create’ but no such parameter
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab.h:57: error: declaration for parameter ‘slab_is_available’ but no such parameter
/usr/src/linux-headers-2.6.27-9-generic/include/linux/slab.h:56: error: declaration for parameter ‘kmem_cache_init’ but no such parameter
/usr/src/linux-headers-2.6.27-9-generic/include/linux/marker.h:160: error: declaration for parameter ‘marker_get_private_data’ but no such parameter
/usr/src/linux-headers-2.6.27-9-generic/include/linux/marker.h:157: error: declaration for parameter ‘marker_probe_unregister_private_data’ but no such parameter
/usr/src/linux-headers-2.6.27-9-generic/include/linux/marker.h:152: error: declaration for parameter ‘marker_probe_unregister’ but no such parameter
/usr/src/linux-headers-2.6.27-9-generic/include/linux/marker.h:146: error: declaration for parameter ‘marker_probe_register’ but no such parameter
/usr/src/linux-headers-2.6.27-9-generic/include/linux/marker.h:139: error: declaration for parameter ‘marker_probe_cb_noarg’ but no such parameter
/usr/src/linux-headers-2.6.27-9-generic/include/linux/marker.h:137: error: declaration for parameter ‘marker_probe_cb’ but no such parameter
/usr/src/linux-headers-2.6.27-9-generic/include/linux/marker.h:135: error: declaration for parameter ‘__mark_empty_function’ but no such parameter
hello.c:12: error: expected ‘{’ at end of input

---

### Post by zilla62 on 2008-12-03
I saw this and installed the build-essential package to no avail.

[http://ubuntuforums.org/showthread.php?t=342211](http://ubuntuforums.org/showthread.php?t=342211)

---

### Post by sedawk on 2008-12-03
I haven't compiled any kernel stuff for a long time,
but the last time I tried it was mandatory to use
the optimization parameter "-O".
I cannot remember which was the one to use, so try with
"-O", "-O0",..., "-O3"

---

### Post by zilla62 on 2008-12-03
Thanks tried that with same result. I'm missing something fundamental.

---

### Post by zilla62 on 2008-12-04
I chopping the error codes little by little by looking at them and adding these, for example, in my *.c file...

#define __ASSEMBLY__
#define __KERNEL_STRICT_NAMES
#define __CHECKER__
#define __CHECK_ENDIAN__
#define MODULE

...etc...

Questions:
1. I'm stuck with /usr/src/linux/include/linux/types.h:180: warning: bitwise attribute directive ignored
/usr/src/linux/include/linux/types.h:180: error: expected , or ; before __le16
/usr/src/linux/include/linux/types.h:181: warning: bitwise attribute directive ignored
/usr/src/linux/include/linux/types.h:182: warning: bitwise attribute directive ignored
/usr/src/linux/include/linux/types.h:182: error: expected , or ; before __le32
/usr/src/linux/include/linux/types.h:183: warning: bitwise attribute directive ignored
/usr/src/linux/include/linux/types.h:185: warning: bitwise attribute directive ignored
/usr/src/linux/include/linux/types.h:185: error: expected , or ; before __

in spite of the #define __CHECKER__ and #define __CHECK_ENDIAN__. Where is __attribute__ #defined?

2. Is there a 'global' way that wraps all these #defines?

---

### Post by zilla62 on 2008-12-04
For thos interested, I found this link that explained everything!

[http://tldp.org/LDP/lkmpg/2.6/html/index.html](http://tldp.org/LDP/lkmpg/2.6/html/index.html)

---

