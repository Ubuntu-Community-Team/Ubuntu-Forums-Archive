---
title: "Banshee crashes."
date: 2006-06-01
forum: Desktop Environments
---

### Post by denisesballs on 2006-06-01
Fresh install of Dapper

```
jesse@dapperdump:~$ sudo apt-get install banshee banshee-daap
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  banshee banshee-daap
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1037kB of archives.
After unpacking 3162kB of additional disk space will be used.
Selecting previously deselected package banshee.
(Reading database ... 106383 files and directories currently installed.)
Unpacking banshee (from .../banshee_0.10.10-0ubuntu10_i386.deb) ...
Selecting previously deselected package banshee-daap.
Unpacking banshee-daap (from .../banshee-daap_0.10.10-0ubuntu10_all.deb) ...
Setting up banshee (0.10.10-0ubuntu10) ...

Setting up banshee-daap (0.10.10-0ubuntu10) ...

jesse@dapperdump:~$ banshee

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries
used by your application.
=================================================================

Stacktrace:


Native stacktrace:

        /usr/lib/libmono.so.0(mono_handle_native_sigsegv+0xe3) [0x4008f43f]
        /usr/lib/libmono.so.0 [0x4005103e]
        /lib/libpthread.so.0 [0x402995ca]
        [0xffffe440]
        [0x41732c3a]
        [0x41732bd9]
        [0x41732823]
        [0x40cd964e]
        /usr/lib/libmono.so.0 [0x4006e438]
        /usr/lib/libmono.so.0(mono_runtime_invoke+0x33) [0x400d0eed]
        /usr/lib/libmono.so.0(mono_runtime_class_init+0x13f) [0x400d312f]
        /usr/lib/libmono.so.0 [0x4006e16e]
        /usr/lib/libmono.so.0(mono_compile_method+0x24) [0x400d1225]
        /usr/lib/libmono.so.0(mono_magic_trampoline+0x1f) [0x400a5b1f]
        [0x40536032]
        [0x4173265a]
        [0x417325f9]
        [0x417322c8]
        [0x41730660]
        [0x4172f6b3]
        [0x41725eca]
        [0x40ce4a63]
        [0x40ce4556]
        [0x40ce42f1]
        [0x40ce41f5]
        [0x40ce41b8]
        [0x40cde616]
        [0x40cd8f95]
        [0x40cd889b]
        [0x40cd8823]
        /usr/lib/libmono.so.0 [0x4006e438]
        /usr/lib/libmono.so.0(mono_runtime_invoke+0x33) [0x400d0eed]
        /usr/lib/libmono.so.0(mono_runtime_exec_main+0x67) [0x400d3a88]
        /usr/lib/libmono.so.0(mono_runtime_run_main+0x188) [0x400d6bf0]
        /usr/lib/libmono.so.0(mono_jit_exec+0x90) [0x40080b5e]
        /usr/lib/libmono.so.0(mono_main+0x962) [0x4008154f]
        /lib/libc.so.6(__libc_start_main+0xa3) [0x4032831f]
        banshee [0x8048459]
Aborted
```

It worked fine on Dapper RC2. What could be different?

---

### Post by denisesballs on 2006-06-02
*BUMP*

anyone else getting this? I had Banshee installed on dapper preview no problem on the exact same machine! Even when building it from source I get the exact same error.

---

### Post by denisesballs on 2006-06-02
Found the answer here - [http://ubuntuforums.org/showthread.php?t=167749](http://ubuntuforums.org/showthread.php?t=167749)

---

