---
title: "Compiling Woes"
date: 2005-12-10
forum: General Help
---

### Post by nelposto on 2005-12-10
Hey... n00b of a week in linux here.

Having some problems with compiling a new Kernel. I originally wanted to try to incorporate Suspend2 into my kernel so that my laptop could hibernate. Problem is that after I compiled the image and added it to grub, selecting it from the menu would result in a blank screen .. and after a few seconds the number lock light would disappear. No activity would be shown by the LEDs, and alt-control-delete would restart the machine.

I thought at first that I must be making a mistake in options I selected for the kernel.. and eventually I found a config of the original options of my working kernel. In the interests of eliminating other possibilities, I tried to compile these options into my own kernel. 

Unfortunately the kernel will not compile, it stops with some errors, which I'd post here but I don't know how to have them logged / retrieve them to post here. The errors were along the lines of missing references or something that it was looking for being missing.

Given the above result, I'm wondering if possibly my compiling tools / associated libraries may be corrupt/broken.

Would it be possible for me to complete remove the tools etc and reinstall them if this were the case?

I also thought about compiling from a live CD... but it doesn't seem to have the make tool. Actually I might have a look in aptitude for that now...

In the meantime, any comments or suggestions would be much appreciated..


* Edit... did find 'make' ... i'll play around with this in Live for a bit and see what I can come up with.. *

---

### Post by amohanty on 2005-12-10
> Unfortunately the kernel will not compile, it stops with some errors, which I'd post here but I don't know how to have them logged / retrieve them to post here. The errors were along the lines of missing references or something that it was looking for being missing.

to send output to a fil while still seeing the o/p of a program use the tee command like so:
for eg

```
make xyz **| tee loggile.txt**
```

add the part in bold and all the output will appear on the screen as well as in the file logfile.txt

HTH

---

### Post by dafl00 on 2005-12-10
[This should help you.]("http://newbiedoc.sourceforge.net/system/kernel-pkg.html")

---

### Post by nelposto on 2005-12-10
Thanks alot to you both..

I think my problem came from a bad blind first attempt at following a HOWTO combined with multiple attempts done differently leading to alot of mixed up things.. symlink issues etc. I'm still getting my head around all this kind of thing.

I cleared out most everything in usr/src and removed/reinstalled source packages.. followed a HOWTO more closely with new knowledge.. and planning on using mkpkg... Compiling now, so we'll see...

Thanks again

---

### Post by nelposto on 2005-12-10
Still having problems compiling the current kernel...

This comes after about half an hour of compiling

[PHP] 
...
 AR      arch/i386/lib/lib.a
  GEN     .version
  CHK     include/linux/compile.h
  UPD     include/linux/compile.h
  CC      init/version.o
  LD      init/built-in.o
  LD      .tmp_vmlinux1

kernel/built-in.o: In function `s2_compress_write_init':
compression.c:(.text+0x18c00): undefined reference to `get_next_filter'
compression.c:(.text+0x18c3d): undefined reference to `bytes_out'
compression.c:(.text+0x18c47): undefined reference to `bytes_in'
kernel/built-in.o: In function `s2_compress_write':
compression.c:(.text+0x18c6f): undefined reference to `bytes_out'
kernel/built-in.o: In function `s2_compress_write_chunk':
compression.c:(.text+0x18d36): undefined reference to `bytes_in'
kernel/built-in.o: In function `s2_compress_read_init':
compression.c:(.text+0x18e75): undefined reference to `get_next_filter'
kernel/built-in.o: In function `s2_compress_print_debug_stats':
compression.c:(.text+0x190ed): undefined reference to `bytes_in'
compression.c:(.text+0x190f7): undefined reference to `bytes_out'
compression.c:(.text+0x1911c): undefined reference to `bytes_out'
compression.c:(.text+0x19122): undefined reference to `bytes_in'
kernel/built-in.o: In function `s2_compress_save_config_info':
compression.c:(.text+0x1916b): undefined reference to `bytes_in'
compression.c:(.text+0x19176): undefined reference to `bytes_out'
kernel/built-in.o: In function `s2_compress_load_config_info':
compression.c:(.text+0x191b7): undefined reference to `bytes_in'
compression.c:(.text+0x191bf): undefined reference to `bytes_out'
kernel/built-in.o: In function `s2_encrypt_write_init':
encryption.c:(.text+0x193cd): undefined reference to `get_next_filter'
encryption.c:(.text+0x19420): undefined reference to `bytes_out'
encryption.c:(.text+0x1942a): undefined reference to `bytes_in'
kernel/built-in.o: In function `s2_encrypt_write_chunk':
encryption.c:(.text+0x1946f): undefined reference to `bytes_in'
kernel/built-in.o: In function `s2_encrypt_read_init':
encryption.c:(.text+0x19507): undefined reference to `get_next_filter'
kernel/built-in.o: In function `s2_compress_load':
compression.c:(.init.text+0xc8d): undefined reference to `suspend_register_plugi n'
compression.c:(.init.text+0xca3): undefined reference to `suspend_register_procf ile'
kernel/built-in.o: In function `s2_encrypt_load':
encryption.c:(.init.text+0xcd4): undefined reference to `suspend_register_plugin '
encryption.c:(.init.text+0xcea): undefined reference to `suspend_register_procfi le'
make: *** [.tmp_vmlinux1] Error 1
[/PHP]

Any help would be appreciated..

---

### Post by nelposto on 2005-12-11
BUMP for an update:

I solved the blank screen problem, which means I can see why my kernels aren't booting...

Errors similar to :

can't load /lib/modules/**kernel folder name**/modules.dep : file not found

even though the file is definitely there.

then it gives a /dev/sda3 cannot be found booting to shell! message.

Of course /dev/sda3 also exists. It's what my working kernel boots from.

---

