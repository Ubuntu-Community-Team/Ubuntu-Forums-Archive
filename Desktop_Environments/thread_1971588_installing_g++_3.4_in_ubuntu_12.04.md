---
title: "installing g++ 3.4 in ubuntu 12.04"
date: 2012-05-02
forum: Desktop Environments
---

### Post by mIXpRo on 2012-05-02
hi,
i need g++ 3.4.6 , so i tried installing it using the .debs in this link :
[HTML]http://packages.ubuntu.com/hardy-updates/g++-3.4[/HTML]
and when i use :
```

sudo dpkg -i ./*.deb

```
 
i get this :

```

Selecting previously unselected package gcc-3.4.
(Reading database ... 189662 files and directories currently installed.)
Unpacking gcc-3.4 (from .../gcc-3.4_3.4.6-6ubuntu5_amd64.deb) ...
Preparing to replace gcc-3.4-base 3.4.6-6ubuntu5 (using .../gcc-3.4-base_3.4.6-6ubuntu5_amd64.deb) ...
Unpacking replacement gcc-3.4-base ...
Preparing to replace gcc-3.4-doc 3.4.6-6ubuntu5 (using .../gcc-3.4-doc_3.4.6-6ubuntu5_all.deb) ...
Unpacking replacement gcc-3.4-doc ...
Selecting previously unselected package lib64stdc++6:i386.
Unpacking lib64stdc++6:i386 (from .../lib64stdc++6_4.2.4-1ubuntu4_i386.deb) ...
dpkg: warning: downgrading libc6 from 2.15-0ubuntu10 to 2.7-10ubuntu8.1.
dpkg: error processing ./libc6_2.7-10ubuntu8.1_amd64.deb (--install):
 libc6:amd64 2.7-10ubuntu8.1 (Multi-Arch: no) is not co-installable with libc6:i386 2.15-0ubuntu10 (Multi-Arch: same) which is currently installed
dpkg: warning: downgrading libstdc++6 from 4.6.3-1ubuntu5 to 4.2.4-1ubuntu4.
dpkg: error processing ./libstdc++6_4.2.4-1ubuntu4_amd64.deb (--install):
 libstdc++6:amd64 4.2.4-1ubuntu4 (Multi-Arch: no) is not co-installable with libstdc++6:i386 4.6.3-1ubuntu5 (Multi-Arch: same) which is currently installed
Selecting previously unselected package libstdc++6-dev.
Unpacking libstdc++6-dev (from .../libstdc++6-dev_3.4.6-6ubuntu5_amd64.deb) ...
dpkg: dependency problems prevent configuration of gcc-3.4:
 gcc-3.4 depends on cpp-3.4 (= 3.4.6-6ubuntu5); however:
  Package cpp-3.4 is not installed.
dpkg: error processing gcc-3.4 (--install):
 dependency problems - leaving unconfigured
Setting up gcc-3.4-base (3.4.6-6ubuntu5) ...
Setting up gcc-3.4-doc (3.4.6-6ubuntu5) ...
Ignoring install-info called from maintainer script
The package gcc-3.4-doc should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package gcc-3.4-doc should be rebuilt with new debhelper to get trigger support
dpkg: dependency problems prevent configuration of lib64stdc++6:i386:
 lib64stdc++6:i386 depends on gcc-4.2-base (= 4.2.4-1ubuntu4).
 lib64stdc++6:i386 depends on lib64gcc1 (>= 1:4.2.1).
dpkg: error processing lib64stdc++6:i386 (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libstdc++6-dev:
 libstdc++6-dev depends on g++-3.4 (= 3.4.6-6ubuntu5); however:
  Package g++-3.4 is not installed.
dpkg: error processing libstdc++6-dev (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Processing triggers for ccache ...
Updating symlinks in /usr/lib/ccache ...
Processing triggers for install-info ...
Processing triggers for doc-base ...
Processing 2 changed doc-base files...
Errors were encountered while processing:
 ./libc6_2.7-10ubuntu8.1_amd64.deb
 ./libstdc++6_4.2.4-1ubuntu4_amd64.deb
 gcc-3.4
 lib64stdc++6:i386
 libstdc++6-dev


```

how can fix this ?? 

thnx .

---

### Post by mc4man on 2012-05-02
You grabbed too many .debs, only 5 are needed - 
```
:~/Desktop/3.4$ ls
cpp-3.4_3.4.6-6ubuntu5_amd64.deb  
gcc-3.4-base_3.4.6-6ubuntu5_amd64.deb
g++-3.4_3.4.6-6ubuntu5_amd64.deb  
libstdc++6-dev_3.4.6-6ubuntu5_amd64.deb
gcc-3.4_3.4.6-6ubuntu5_amd64.deb

```

> :~/Desktop/3.4$ sudo dpkg -i *.deb
[sudo] password for doug: 
Selecting previously unselected package cpp-3.4.
(Reading database ... 204046 files and directories currently installed.)
Unpacking cpp-3.4 (from cpp-3.4_3.4.6-6ubuntu5_amd64.deb) ...
Selecting previously unselected package g++-3.4.
Unpacking g++-3.4 (from g++-3.4_3.4.6-6ubuntu5_amd64.deb) ...
Selecting previously unselected package gcc-3.4.
Unpacking gcc-3.4 (from gcc-3.4_3.4.6-6ubuntu5_amd64.deb) ...
Selecting previously unselected package gcc-3.4-base.
Unpacking gcc-3.4-base (from gcc-3.4-base_3.4.6-6ubuntu5_amd64.deb) ...
Selecting previously unselected package libstdc++6-dev.
Unpacking libstdc++6-dev (from libstdc++6-dev_3.4.6-6ubuntu5_amd64.deb) ...
Setting up gcc-3.4-base (3.4.6-6ubuntu5) ...
Setting up cpp-3.4 (3.4.6-6ubuntu5) ...
Processing triggers for man-db ...
Setting up gcc-3.4 (3.4.6-6ubuntu5) ...
Setting up g++-3.4 (3.4.6-6ubuntu5) ...
Setting up libstdc++6-dev (3.4.6-6ubuntu5) ...
doug@doug-XPS-M1330:~/Desktop/3.4$ 


---

### Post by mIXpRo on 2012-05-03
i'v install it , like you suggested .
now when i compile a project i get this :
 note : i used g++-3.4 , and i have no g++ installed 

```

naseem@naseem-pc:/media/6221-E854/oop2_C$ g++-3.4 -o oop ./*
gcc-opt: Failed to open /CurrentlyBuilding
./IteratorImpl.h:3: error: `cs236703_spring2012_hw2' is not a namespace-name
./IteratorImpl.h:3: error: expected namespace-name before ';' token
./IteratorImpl.h:7: error: expected class-name before '{' token
./IteratorImpl.h:10: error: ISO C++ forbids declaration of `Node' with no type
./IteratorImpl.h:10: error: expected `;' before '*' token
./IteratorImpl.h:11: error: ISO C++ forbids declaration of `Node' with no type
./IteratorImpl.h:11: error: expected `;' before '*' token
./IteratorImpl.h:19: error: `Node' has not been declared
./IteratorImpl.h:19: error: ISO C++ forbids declaration of `next' with no type
./IteratorImpl.h:20: error: ISO C++ forbids declaration of `Node' with no type
./IteratorImpl.h:20: error: expected `;' before '*' token
./IteratorImpl.h:21: error: `Node' has not been declared
./IteratorImpl.h:21: error: ISO C++ forbids declaration of `prev' with no type
./IteratorImpl.h:22: error: ISO C++ forbids declaration of `Node' with no type
./IteratorImpl.h:22: error: expected `;' before '*' token
./IteratorImpl.h:30: error: expected class-name before '{' token
./IteratorImpl.h:31: error: ISO C++ forbids declaration of `Node' with no type
./IteratorImpl.h:31: error: expected `;' before '*' token
./IteratorImpl.h:32: error: ISO C++ forbids declaration of `Node' with no type
./IteratorImpl.h:32: error: expected `;' before '*' token
./IteratorImpl.h:40: error: ISO C++ forbids declaration of `Iterator' with no type
./IteratorImpl.h:40: error: expected `;' before '*' token
./IteratorImpl.h:49: error: expected class-name before '{' token
./IteratorImpl.h:52: error: ISO C++ forbids declaration of `Node' with no type
./IteratorImpl.h:52: error: expected `;' before '*' token
```


i get this although i compiled it on distro which its default g++ is g++ 3.4.6 and it compiled fine .

can you explain ,please ?

thanx .

---

### Post by mIXpRo on 2012-05-04
can someone please , help , i need this

---

### Post by mIXpRo on 2012-06-06
i've tried to compile this :
> 
#include <stdio.h>

int main(){
	printf("hisss     \n");

	return 0;
}

in gcc works but gcc-3.4 i get :
> 
In file included from /usr/include/stdio.h:28,
                 from ./hi.c:1:
/usr/include/features.h:324:26: bits/predefs.h: No such file or directory
/usr/include/features.h:357:25: sys/cdefs.h: No such file or directory
/usr/include/features.h:389:23: gnu/stubs.h: No such file or directory
In file included from /usr/include/stdio.h:34,
                 from ./hi.c:1:
/usr/lib/gcc/i486-linux-gnu/3.4.6/include/stddef.h:213: error: syntax error before "typedef"
In file included from ./hi.c:1:
/usr/include/stdio.h:36:25: bits/types.h: No such file or directory
In file included from ./hi.c:1:
/usr/include/stdio.h:49: error: syntax error before "typedef"
/usr/include/stdio.h:54: error: syntax error before "__USING_NAMESPACE_STD"
/usr/include/stdio.h: In function `__USING_NAMESPACE_STD':
/usr/include/stdio.h:65: error: storage class specified for parameter `__FILE'
In file included from /usr/include/_G_config.h:20,
                 from /usr/include/libio.h:32,
                 from /usr/include/stdio.h:75,
                 from ./hi.c:1:
/usr/include/wchar.h:95: error: storage class specified for parameter `__mbstate_t'
In file included from /usr/include/libio.h:32,
                 from /usr/include/stdio.h:75,
                 from ./hi.c:1:
/usr/include/_G_config.h:24: error: syntax error before "__off_t"
/usr/include/_G_config.h:29: error: syntax error before "__off64_t"
/usr/include/_G_config.h:53: error: storage class specified for parameter `_G_int16_t'
/usr/include/_G_config.h:54: error: storage class specified for parameter `_G_int32_t'
/usr/include/_G_config.h:55: error: storage class specified for parameter `_G_uint16_t'
/usr/include/_G_config.h:56: error: storage class specified for parameter `_G_uint32_t'
In file included from /usr/include/libio.h:53,
                 from /usr/include/stdio.h:75,
                 from ./hi.c:1:
/usr/lib/gcc/i486-linux-gnu/3.4.6/include/stdarg.h:43: error: storage class specified for parameter `__gnuc_va_list'
In file included from /usr/include/stdio.h:75,
                 from ./hi.c:1:
/usr/include/libio.h:182: error: storage class specified for parameter `_IO_lock_t'
/usr/include/libio.h:302: error: syntax error before "__off_t"
/usr/include/libio.h:312: error: syntax error before "_IO_lock_t"
/usr/include/libio.h:340: error: syntax error before '}' token
/usr/include/libio.h:343: error: storage class specified for parameter `_IO_FILE'
/usr/include/libio.h:348: error: storage class specified for parameter `_IO_2_1_stdin_'
/usr/include/libio.h:349: error: storage class specified for parameter `_IO_2_1_stdout_'
/usr/include/libio.h:350: error: storage class specified for parameter `_IO_2_1_stderr_'
/usr/include/libio.h:366: error: storage class specified for parameter `__ssize_t'
/usr/include/libio.h:366: error: syntax error before "__io_read_fn"
/usr/include/libio.h:374: error: storage class specified for parameter `__ssize_t'
/usr/include/libio.h:374: error: redefinition of parameter '__ssize_t'
/usr/include/libio.h:366: error: previous definition of '__ssize_t' was here
/usr/include/libio.h:374: error: syntax error before "__io_write_fn"
/usr/include/libio.h:383: error: syntax error before "__off64_t"
/usr/include/libio.h:383: error: storage class specified for parameter `__io_seek_fn'
/usr/include/libio.h:386: error: storage class specified for parameter `__io_close_fn'
/usr/include/libio.h:418: error: syntax error before '*' token
/usr/include/libio.h:418: error: storage class specified for parameter `__underflow'
/usr/include/libio.h:419: error: syntax error before '*' token
/usr/include/libio.h:419: error: storage class specified for parameter `__uflow'
/usr/include/libio.h:420: error: syntax error before '*' token
/usr/include/libio.h:420: error: storage class specified for parameter `__overflow'
/usr/include/libio.h:462: error: syntax error before '*' token
/usr/include/libio.h:462: error: storage class specified for parameter `_IO_getc'
/usr/include/libio.h:463: error: syntax error before "_IO_FILE"
/usr/include/libio.h:463: error: storage class specified for parameter `_IO_putc'
/usr/include/libio.h:464: error: syntax error before '*' token
/usr/include/libio.h:464: error: storage class specified for parameter `_IO_feof'
/usr/include/libio.h:465: error: syntax error before '*' token
/usr/include/libio.h:465: error: storage class specified for parameter `_IO_ferror'
/usr/include/libio.h:467: error: syntax error before '*' token
/usr/include/libio.h:467: error: storage class specified for parameter `_IO_peekc_locked'
/usr/include/libio.h:473: error: syntax error before '*' token
/usr/include/libio.h:473: error: storage class specified for parameter `_IO_flockfile'
/usr/include/libio.h:474: error: syntax error before '*' token
/usr/include/libio.h:474: error: storage class specified for parameter `_IO_funlockfile'
/usr/include/libio.h:475: error: syntax error before '*' token
/usr/include/libio.h:475: error: storage class specified for parameter `_IO_ftrylockfile'
/usr/include/libio.h:492: error: syntax error before '*' token
/usr/include/libio.h:493: error: storage class specified for parameter `_IO_vfscanf'
/usr/include/libio.h:494: error: syntax error before '*' token
/usr/include/libio.h:495: error: storage class specified for parameter `_IO_vfprintf'
/usr/include/libio.h:496: error: storage class specified for parameter `__ssize_t'
/usr/include/libio.h:496: error: redefinition of parameter '__ssize_t'
/usr/include/libio.h:374: error: previous definition of '__ssize_t' was here
/usr/include/libio.h:496: error: syntax error before "_IO_padn"
/usr/include/libio.h:497: error: syntax error before '*' token
/usr/include/libio.h:497: error: storage class specified for parameter `_IO_sgetn'
/usr/include/libio.h:499: error: storage class specified for parameter `__off64_t'
/usr/include/libio.h:499: error: syntax error before "_IO_seekoff"
/usr/include/libio.h:500: error: storage class specified for parameter `__off64_t'
/usr/include/libio.h:500: error: redefinition of parameter '__off64_t'
/usr/include/libio.h:499: error: previous definition of '__off64_t' was here
/usr/include/libio.h:500: error: syntax error before "_IO_seekpos"
/usr/include/libio.h:502: error: syntax error before '*' token
/usr/include/libio.h:502: error: storage class specified for parameter `_IO_free_backup_area'
In file included from ./hi.c:1:
/usr/include/stdio.h:80: error: storage class specified for parameter `__gnuc_va_list'
/usr/include/stdio.h:80: error: conflicting types for '__gnuc_va_list'
/usr/lib/gcc/i486-linux-gnu/3.4.6/include/stdarg.h:43: error: previous definition of '__gnuc_va_list' was here
/usr/include/stdio.h:80: error: syntax error before "va_list"
/usr/include/stdio.h:91: error: storage class specified for parameter `__off_t'
/usr/include/stdio.h:91: error: syntax error before "off_t"
/usr/include/stdio.h:103: error: storage class specified for parameter `__ssize_t'
/usr/include/stdio.h:103: error: redefinition of parameter '__ssize_t'
/usr/include/libio.h:496: error: previous definition of '__ssize_t' was here
/usr/include/stdio.h:103: error: syntax error before "ssize_t"
/usr/include/stdio.h:165:28: bits/stdio_lim.h: No such file or directory
/usr/include/stdio.h:170: error: storage class specified for parameter `stdout'
/usr/include/stdio.h:171: error: storage class specified for parameter `stderr'
/usr/include/stdio.h:177: error: syntax error before "__BEGIN_NAMESPACE_STD"
/usr/include/stdio.h:181: error: storage class specified for parameter `rename'
/usr/include/stdio.h:181: error: syntax error before "__THROW"
/usr/include/stdio.h:210: error: storage class specified for parameter `tmpnam'
/usr/include/stdio.h:210: error: syntax error before "__THROW"
/usr/include/stdio.h:229: error: storage class specified for parameter `tempnam'
/usr/include/stdio.h:229: error: syntax error before "__THROW"
/usr/include/stdio.h:243: error: storage class specified for parameter `fflush'
/usr/include/stdio.h:244: error: syntax error before "__END_NAMESPACE_STD"
/usr/include/stdio.h:281: error: storage class specified for parameter `freopen'
/usr/include/stdio.h:281: error: syntax error before "__wur"
/usr/include/stdio.h:321: error: storage class specified for parameter `fmemopen'
/usr/include/stdio.h:321: error: syntax error before "__THROW"
/usr/include/stdio.h:326: error: storage class specified for parameter `open_memstream'
/usr/include/stdio.h:326: error: syntax error before "__THROW"
/usr/include/stdio.h:338: error: storage class specified for parameter `setvbuf'
/usr/include/stdio.h:338: error: syntax error before "__THROW"
/usr/include/stdio.h:348: error: storage class specified for parameter `setlinebuf'
/usr/include/stdio.h:348: error: syntax error before "__THROW"
/usr/include/stdio.h:363: error: storage class specified for parameter `printf'
/usr/include/stdio.h:366: error: storage class specified for parameter `sprintf'
/usr/include/stdio.h:366: error: syntax error before "__THROWNL"
/usr/include/stdio.h:373: error: syntax error before "__gnuc_va_list"
/usr/include/stdio.h:373: error: storage class specified for parameter `vfprintf'
/usr/include/stdio.h:378: error: syntax error before "__gnuc_va_list"
/usr/include/stdio.h:378: error: storage class specified for parameter `vprintf'
/usr/include/stdio.h:381: error: syntax error before "__gnuc_va_list"
/usr/include/stdio.h:381: error: storage class specified for parameter `vsprintf'
/usr/include/stdio.h:392: error: syntax error before "__gnuc_va_list"
/usr/include/stdio.h:393: error: storage class specified for parameter `vsnprintf'
/usr/include/stdio.h:422: error: storage class specified for parameter `dprintf'
/usr/include/stdio.h:426: error: syntax error before "__BEGIN_NAMESPACE_STD"
/usr/include/stdio.h:437: error: storage class specified for parameter `scanf'
/usr/include/stdio.h:437: error: syntax error before "__wur"
/usr/include/stdio.h:440: error: storage class specified for parameter `sscanf'
/usr/include/stdio.h:440: error: syntax error before "__THROW"
/usr/include/stdio.h:459: error: storage class specified for parameter `__isoc99_fscanf'
/usr/include/stdio.h:459: error: syntax error before "__wur"
/usr/include/stdio.h:460: error: storage class specified for parameter `__isoc99_scanf'
/usr/include/stdio.h:460: error: syntax error before "__wur"
/usr/include/stdio.h:462: error: storage class specified for parameter `__isoc99_sscanf'
/usr/include/stdio.h:462: error: syntax error before "__THROW"
/usr/include/stdio.h:485: error: syntax error before "__gnuc_va_list"
/usr/include/stdio.h:486: error: storage class specified for parameter `vscanf'
/usr/include/stdio.h:486: error: syntax error before "__wur"
/usr/include/stdio.h:490: error: syntax error before "__gnuc_va_list"
/usr/include/stdio.h:491: error: storage class specified for parameter `vsscanf'
/usr/include/stdio.h:516: error: syntax error before "__gnuc_va_list"
/usr/include/stdio.h:516: error: storage class specified for parameter `__isoc99_vfscanf'
/usr/include/stdio.h:518: error: syntax error before "__gnuc_va_list"
/usr/include/stdio.h:518: error: storage class specified for parameter `__isoc99_vscanf'
/usr/include/stdio.h:521: error: syntax error before "__gnuc_va_list"
/usr/include/stdio.h:521: error: storage class specified for parameter `__isoc99_vsscanf'
/usr/include/stdio.h:538: error: storage class specified for parameter `getc'
/usr/include/stdio.h:544: error: storage class specified for parameter `getchar'
/usr/include/stdio.h:545: error: syntax error before "__END_NAMESPACE_STD"
/usr/include/stdio.h:557: error: storage class specified for parameter `getchar_unlocked'
/usr/include/stdio.h:567: error: storage class specified for parameter `fgetc_unlocked'
/usr/include/stdio.h:571: error: syntax error before "__BEGIN_NAMESPACE_STD"
/usr/include/stdio.h:580: error: storage class specified for parameter `putc'
/usr/include/stdio.h:586: error: storage class specified for parameter `putchar'
/usr/include/stdio.h:587: error: syntax error before "__END_NAMESPACE_STD"
/usr/include/stdio.h:608: error: storage class specified for parameter `putc_unlocked'
/usr/include/stdio.h:609: error: storage class specified for parameter `putchar_unlocked'
/usr/include/stdio.h:616: error: storage class specified for parameter `getw'
/usr/include/stdio.h:619: error: storage class specified for parameter `putw'
/usr/include/stdio.h:623: error: syntax error before "__BEGIN_NAMESPACE_STD"
/usr/include/stdio.h:636: error: storage class specified for parameter `gets'
/usr/include/stdio.h:636: error: syntax error before "__wur"
/usr/include/stdio.h:665: error: storage class specified for parameter `__ssize_t'
/usr/include/stdio.h:665: error: redefinition of parameter '__ssize_t'
/usr/include/stdio.h:103: error: previous definition of '__ssize_t' was here
/usr/include/stdio.h:665: error: syntax error before "getdelim"
/usr/include/stdio.h:675: error: storage class specified for parameter `__ssize_t'
/usr/include/stdio.h:675: error: redefinition of parameter '__ssize_t'
/usr/include/stdio.h:665: error: previous definition of '__ssize_t' was here
/usr/include/stdio.h:675: error: syntax error before "getline"
/usr/include/stdio.h:692: error: storage class specified for parameter `puts'
/usr/include/stdio.h:699: error: storage class specified for parameter `ungetc'
/usr/include/stdio.h:707: error: storage class specified for parameter `fread'
/usr/include/stdio.h:707: error: syntax error before "__wur"
/usr/include/stdio.h:713: error: storage class specified for parameter `fwrite'
/usr/include/stdio.h:714: error: syntax error before "__END_NAMESPACE_STD"
/usr/include/stdio.h:737: error: storage class specified for parameter `fwrite_unlocked'
/usr/include/stdio.h:741: error: syntax error before "__BEGIN_NAMESPACE_STD"
/usr/include/stdio.h:751: error: storage class specified for parameter `ftell'
/usr/include/stdio.h:751: error: syntax error before "__wur"
/usr/include/stdio.h:756: error: storage class specified for parameter `rewind'
/usr/include/stdio.h:757: error: syntax error before "__END_NAMESPACE_STD"
/usr/include/stdio.h:775: error: storage class specified for parameter `__off_t'
/usr/include/stdio.h:775: error: redefinition of parameter '__off_t'
/usr/include/stdio.h:91: error: previous definition of '__off_t' was here
/usr/include/stdio.h:775: error: syntax error before "ftello"
/usr/include/stdio.h:800: error: syntax error before '*' token
/usr/include/stdio.h:800: error: storage class specified for parameter `fsetpos'
/usr/include/stdio.h:825: error: storage class specified for parameter `feof'
/usr/include/stdio.h:825: error: syntax error before "__THROW"
/usr/include/stdio.h:827: error: storage class specified for parameter `ferror'
/usr/include/stdio.h:827: error: syntax error before "__THROW"
/usr/include/stdio.h:833: error: storage class specified for parameter `feof_unlocked'
/usr/include/stdio.h:833: error: syntax error before "__THROW"
/usr/include/stdio.h:834: error: storage class specified for parameter `ferror_unlocked'
/usr/include/stdio.h:834: error: syntax error before "__THROW"
/usr/include/stdio.h:850:30: bits/sys_errlist.h: No such file or directory
/usr/include/stdio.h:860: error: storage class specified for parameter `fileno_unlocked'
/usr/include/stdio.h:860: error: syntax error before "__THROW"
/usr/include/stdio.h:870: error: storage class specified for parameter `popen'
/usr/include/stdio.h:870: error: syntax error before "__wur"
/usr/include/stdio.h:876: error: storage class specified for parameter `pclose'
/usr/include/stdio.h:882: error: storage class specified for parameter `ctermid'
/usr/include/stdio.h:882: error: syntax error before "__THROW"
/usr/include/stdio.h:910: error: storage class specified for parameter `flockfile'
/usr/include/stdio.h:910: error: syntax error before "__THROW"
/usr/include/stdio.h:914: error: storage class specified for parameter `ftrylockfile'
/usr/include/stdio.h:914: error: syntax error before "__THROW"
/usr/include/stdio.h:917: error: storage class specified for parameter `funlockfile'
/usr/include/stdio.h:917: error: syntax error before "__THROW"



what should i do ??

---

### Post by mark allyn on 2012-09-19
Hello everyone,
 
I have experienced the same problem as MixPro.  I am using 12.04.  I have installed gcc-4.6 as well as gcc-3.4.  gcc-4.6 compiles without a complaint and links a usable executable.  The problem MixPro and I have comes from gcc-3.6.  
 
Can someone advise us how to fix the problem.
 
Regards,
Mark Allyn

---

### Post by alexmatos.br on 2012-09-21
I solve part of problem with this:

> export LIBRARY_PATH=/usr/lib/i386-linux-gnu
export C_INCLUDE_PATH=/usr/include/i386-linux-gnu
export CPLUS_INCLUDE_PATH=/usr/include/i386-linux-gnu
[http://gcc.gnu.org/ml/gcc/2012-06/msg00095.html]("http://gcc.gnu.org/ml/gcc/2012-06/msg00095.html")

But still appears:
```
gcc-opt: Failed to open /CurrentlyBuilding
```

---

