---
title: "Help with simple kernel module build"
date: 2008-12-03
forum: General Help
---

### Post by zilla62 on 2008-12-03
I'm trying to build this simple file (from Alessandro Rubini's Linux Device Drivers book).

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

I do....
> gcc -c -I/usr/src/linux-headers-2.6.27-9/include hello.c

or...
> gcc -c -I/usr/src/linux-headers-2.6.27-9-generic/include hello.c

and get the following errors; I'm obviousle missing a path?

/usr/src/linux-headers-2.6.27-9/include/linux/mutex.h:50: error: expected specifier-qualifier-list before ‘atomic_t’
/usr/src/linux-headers-2.6.27-9/include/linux/mutex.h: In function ‘mutex_is_locked’:
/usr/src/linux-headers-2.6.27-9/include/linux/mutex.h:117: error: ‘struct mutex’ has no member named ‘count’
/usr/src/linux-headers-2.6.27-9/include/linux/mutex.h: At top level:
/usr/src/linux-headers-2.6.27-9/include/linux/mutex.h:136: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘mutex_lock_interruptible’
/usr/src/linux-headers-2.6.27-9/include/linux/mutex.h:137: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘mutex_lock_killable’
In file included from /usr/src/linux-headers-2.6.27-9/include/linux/notifier.h:14,
                 from /usr/src/linux-headers-2.6.27-9/include/linux/memory_hotplug.h:6,
                 from /usr/src/linux-headers-2.6.27-9/include/linux/mmzone.h:560,
                 from /usr/src/linux-headers-2.6.27-9/include/linux/gfp.h:4,
                 from /usr/src/linux-headers-2.6.27-9/include/linux/kmod.h:22,
                 from /usr/src/linux-headers-2.6.27-9/include/linux/module.h:13,
                 from hello.c:2:
/usr/src/linux-headers-2.6.27-9/include/linux/rwsem.h:22:65: error: asm/rwsem.h: No such file or directory
In file included from /usr/src/linux-headers-2.6.27-9/include/linux/memory_hotplug.h:6,
                 from /usr/src/linux-headers-2.6.27-9/include/linux/mmzone.h:560,
                 from /usr/src/linux-headers-2.6.27-9/include/linux/gfp.h:4,
                 from /usr/src/linux-headers-2.6.27-9/include/linux/kmod.h:22,
                 from /usr/src/linux-headers-2.6.27-9/include/linux/module.h:13,
                 from hello.c:2:
/usr/src/linux-headers-2.6.27-9/include/linux/notifier.h:62: error: field ‘rwsem’ has incomplete type
In file included from /usr/src/linux-headers-2.6.27-9/include/linux/mmzone.h:560,
                 from /usr/src/linux-headers-2.6.27-9/include/linux/gfp.h:4,
                 from /usr/src/linux-headers-2.6.27-9/include/linux/kmod.h:22,
                 from /usr/src/linux-headers-2.6.27-9/include/linux/module.h:13,
                 from hello.c:2:
/usr/src/linux-headers-2.6.27-9/include/linux/memory_hotplug.h: In function ‘mhp_notimplemented’:
/usr/src/linux-headers-2.6.27-9/include/linux/memory_hotplug.h:183: error: ‘KERN_WARNING’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.27-9/include/linux/memory_hotplug.h:183: error: expected ‘)’ before string constant
/usr/src/linux-headers-2.6.27-9/include/linux/memory_hotplug.h: At top level:
/usr/src/linux-headers-2.6.27-9/include/linux/memory_hotplug.h:214: error: expected declaration specifiers or ‘...’ before ‘u64’
/usr/src/linux-headers-2.6.27-9/include/linux/memory_hotplug.h:214: error: expected declaration specifiers or ‘...’ before ‘u64’
/usr/src/linux-headers-2.6.27-9/include/linux/memory_hotplug.h:215: error: expected declaration specifiers or ‘...’ before ‘u64’
/usr/src/linux-headers-2.6.27-9/include/linux/memory_hotplug.h:215: error: expected declaration specifiers or ‘...’ before ‘u64’
/usr/src/linux-headers-2.6.27-9/include/linux/memory_hotplug.h:216: error: expected ‘)’ before ‘start’
In file included from /usr/src/linux-headers-2.6.27-9/include/linux/gfp.h:4,
                 from /usr/src/linux-headers-2.6.27-9/include/linux/kmod.h:22,
                 from /usr/src/linux-headers-2.6.27-9/include/linux/module.h:13,
                 from hello.c:2:
/usr/src/linux-headers-2.6.27-9/include/linux/mmzone.h: In function ‘populated_zone’:
/usr/src/linux-headers-2.6.27-9/include/linux/mmzone.h:593: error: ‘struct zone’ has no member named ‘present_pages’
/usr/src/linux-headers-2.6.27-9/include/linux/mmzone.h: In function ‘is_normal’:
/usr/src/linux-headers-2.6.27-9/include/linux/mmzone.h:642: error: ‘struct zone’ has no member named ‘zone_pgdat’
/usr/src/linux-headers-2.6.27-9/include/linux/mmzone.h: At top level:
/usr/src/linux-headers-2.6.27-9/include/linux/mmzone.h:667: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/usr/src/linux-headers-2.6.27-9/include/linux/mmzone.h:670: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/usr/src/linux-headers-2.6.27-9/include/linux/mmzone.h:672: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/usr/src/linux-headers-2.6.27-9/include/linux/mmzone.h:674: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/usr/src/linux-headers-2.6.27-9/include/linux/mmzone.h:676: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/usr/src/linux-headers-2.6.27-9/include/linux/mmzone.h:679: error: expected declaration specifiers or ‘...’ before ‘loff_t’
In file included from /usr/src/linux-headers-2.6.27-9/include/linux/topology.h:30,
                 from /usr/src/linux-headers-2.6.27-9/include/linux/mmzone.h:683,
                 from /usr/src/linux-headers-2.6.27-9/include/linux/gfp.h:4,
                 from /usr/src/linux-headers-2.6.27-9/include/linux/kmod.h:22,
                 from /usr/src/linux-headers-2.6.27-9/include/linux/module.h:13,
                 from hello.c:2:
/usr/src/linux-headers-2.6.27-9/include/linux/cpumask.h:141: error: expected specifier-qualifier-list before ‘DECLARE_BITMAP’
/usr/src/linux-headers-2.6.27-9/include/linux/cpumask.h: In function ‘__cpu_set’:
/usr/src/linux-headers-2.6.27-9/include/linux/cpumask.h:147: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9/include/linux/cpumask.h: In function ‘__cpu_clear’:
/usr/src/linux-headers-2.6.27-9/include/linux/cpumask.h:153: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9/include/linux/cpumask.h: In function ‘__cpus_setall’:
/usr/src/linux-headers-2.6.27-9/include/linux/cpumask.h:159: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9/include/linux/cpumask.h: In function ‘__cpus_clear’:
/usr/src/linux-headers-2.6.27-9/include/linux/cpumask.h:165: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9/include/linux/cpumask.h: In function ‘__cpu_test_and_set’:
/usr/src/linux-headers-2.6.27-9/include/linux/cpumask.h:174: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9/include/linux/cpumask.h: In function ‘__cpus_and’:
/usr/src/linux-headers-2.6.27-9/include/linux/cpumask.h:181: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9/include/linux/cpumask.h:181: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9/include/linux/cpumask.h:181: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9/include/linux/cpumask.h: In function ‘__cpus_or’:
/usr/src/linux-headers-2.6.27-9/include/linux/cpumask.h:188: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9/include/linux/cpumask.h:188: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9/include/linux/cpumask.h:188: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9/include/linux/cpumask.h: In function ‘__cpus_xor’:
/usr/src/linux-headers-2.6.27-9/include/linux/cpumask.h:195: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9/include/linux/cpumask.h:195: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9/include/linux/cpumask.h:195: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9/include/linux/cpumask.h: In function ‘__cpus_andnot’:
/usr/src/linux-headers-2.6.27-9/include/linux/cpumask.h:203: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9/include/linux/cpumask.h:203: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.27-9/include/linux/cpumask.h:203: error: ‘cpumask_t’

---

### Post by zilla62 on 2008-12-03
I'm trying to build this simple file (from Alessandro Rubini's Linux Device Drivers book).

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

I do....
> gcc -c -I/usr/src/linux-headers-2.6.27-9/include hello.c

or...
> gcc -c -I/usr/src/linux-headers-2.6.27-9-generic/include hello.c

and get the following errors; I'm obviousle missing a path?
(snipped)
/usr/src/linux-headers-2.6.27-9/include/linux/mutex.h:50: error: expected specifier-qualifier-list before ‘atomic_t’
/usr/src/linux-headers-2.6.27-9/include/linux/mutex.h: In function ‘mutex_is_locked’:
/usr/src/linux-headers-2.6.27-9/include/linux/mutex.h:117: error: ‘struct mutex’ has no member named ‘count’
/usr/src/linux-headers-2.6.27-9/include/linux/mutex.h: At top level:
(snipped)

---

