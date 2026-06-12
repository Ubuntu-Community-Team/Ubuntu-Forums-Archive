---
title: "Anone else having trouble w/ XMMS after upgrade?"
date: 2005-10-22
forum: Desktop Environments
---

### Post by gomer on 2005-10-22
I just upgraded from hoary to breezy, and now, xmms seg faults on me. doesn't dump core, just seg faults. I'm not sure what's going on. I haven't tried rolling my own bonary to see if maybe it's a bad binary or something, though.

gomer@io:~ $ xmms
Segmentation fault

Has this happened to anyone else?

--Gomer

---

### Post by taurus on 2005-10-22
See what's the output when you run

ldd /usr/bin/xmms
(assuming that xmms is in /usr/bin...)

---

### Post by Muiske on 2005-10-25
@gomer: I have the *exact* problem. XMMS just stopped working, all of a sudden. Equake as well... I have opened a thread about this in the gaming section of this forum. I think, somehow, these two problems might be related by some strange rapture in the space/time fabric.


[QUOTE=taurus]See what's the output when you run

ldd /usr/bin/xmms
(assuming that xmms is in /usr/bin...)[/QUOTE]


I have done just that. Here's the output:

```
linux-gate.so.1 =>  (0xffffe000)
        libSM.so.6 => /usr/lib/libSM.so.6 (0xb7f0d000)
        libICE.so.6 => /usr/lib/libICE.so.6 (0xb7ef4000)
        libxmms.so.1 => /usr/lib/libxmms.so.1 (0xb7ee7000)
        libgtk-1.2.so.0 => /usr/lib/libgtk-1.2.so.0 (0xb7dac000)
        libgdk-1.2.so.0 => /usr/lib/libgdk-1.2.so.0 (0xb7d75000)
        libgmodule-1.2.so.0 => /usr/lib/libgmodule-1.2.so.0 (0xb7d71000)
        libgthread-1.2.so.0 => /usr/lib/libgthread-1.2.so.0 (0xb7d6e000)
        libglib-1.2.so.0 => /usr/lib/libglib-1.2.so.0 (0xb7d4a000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7d38000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7d35000)
        libXi.so.6 => /usr/lib/libXi.so.6 (0xb7d2d000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7d1f000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7c5f000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7c3d000)
        libssl.so.0.9.7 => /usr/lib/i686/cmov/libssl.so.0.9.7 (0xb7c0d000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7adf000)
        /lib/ld-linux.so.2 (0xb7f29000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7adb000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7ad7000)
        libcrypto.so.0.9.7 => /usr/lib/i686/cmov/libcrypto.so.0.9.7 (0xb79da000)

```


strace -f xmms returns with this:

```
[pid  9216] open("/usr/lib/xmms/Visualization", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY ) = 7
[pid  9216] fstat64(7, {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
[pid  9216] fcntl64(7, F_SETFD, FD_CLOEXEC) = 0
[pid  9216] getdents64(7, /* 11 entries */, 4096) = 384
[pid  9216] stat64("/usr/lib/xmms/Visualization/.", {st_mode=S_IFDIR|0755, st_size=4096, .. .}) = 0
[pid  9216] stat64("/usr/lib/xmms/Visualization/..", {st_mode=S_IFDIR|0755, st_size=4096, . ..}) = 0
[pid  9216] stat64("/usr/lib/xmms/Visualization/libogl_spectrum.so", {st_mode=S_IFREG|0644,  st_size=19132, ...}) = 0
[pid  9216] open("/usr/lib/xmms/Visualization/libogl_spectrum.so", O_RDONLY) = 8
[pid  9216] read(8, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\220\36"..., 512) = 512
[pid  9216] fstat64(8, {st_mode=S_IFREG|0644, st_size=19132, ...}) = 0
[pid  9216] old_mmap(NULL, 23300, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 8, 0) = 0 xb6d8b000
[pid  9216] old_mmap(0xb6d90000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENY WRITE, 8, 0x4000) = 0xb6d90000
[pid  9216] close(8)                    = 0
[pid  9216] open("/etc/ld.so.cache", O_RDONLY) = 8
[pid  9216] fstat64(8, {st_mode=S_IFREG|0644, st_size=71208, ...}) = 0
[pid  9216] old_mmap(NULL, 71208, PROT_READ, MAP_PRIVATE, 8, 0) = 0xb6d79000
[pid  9216] close(8)                    = 0
[pid  9216] access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
[pid  9216] open("/usr/lib/libGL.so.1", O_RDONLY) = 8
[pid  9216] read(8, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\360\234"..., 512) = 51 2
[pid  9216] fstat64(8, {st_mode=S_IFREG|0644, st_size=515012, ...}) = 0
[pid  9216] old_mmap(NULL, 519392, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 8, 0) = 0xb6cfa000
[pid  9216] old_mmap(0xb6d60000, 98304, PROT_READ|PROT_WRITE|PROT_EXEC, MAP_PRIVATE|MAP_FIX ED|MAP_DENYWRITE, 8, 0x66000) = 0xb6d60000
[pid  9216] old_mmap(0xb6d78000, 3296, PROT_READ|PROT_WRITE|PROT_EXEC, MAP_PRIVATE|MAP_FIXE D|MAP_ANONYMOUS, -1, 0) = 0xb6d78000
[pid  9216] close(8)                    = 0
[pid  9216] access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
[pid  9216] open("/usr/lib/libGLcore.so.1", O_RDONLY) = 8
[pid  9216] read(8, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\200Z\v"..., 512) = 512
[pid  9216] fstat64(8, {st_mode=S_IFREG|0644, st_size=7754112, ...}) = 0
[pid  9216] old_mmap(NULL, 7768964, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 8, 0) =  0xb6591000
[pid  9216] old_mmap(0xb6cc4000, 204800, PROT_READ|PROT_WRITE|PROT_EXEC, MAP_PRIVATE|MAP_FI XED|MAP_DENYWRITE, 8, 0x733000) = 0xb6cc4000
[pid  9216] old_mmap(0xb6cf6000, 15236, PROT_READ|PROT_WRITE|PROT_EXEC, MAP_PRIVATE|MAP_FIX ED|MAP_ANONYMOUS, -1, 0) = 0xb6cf6000
[pid  9216] close(8)                    = 0
[pid  9216] access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
[pid  9216] open("/usr/lib/libnvidia-tls.so.1", O_RDONLY) = 8
[pid  9216] read(8, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P\3\0\000"..., 512) = 5 12
[pid  9216] lseek(8, 1304, SEEK_SET)    = 1304
[pid  9216] read(8, "\4\0\0\0\20\0\0\0\1\0\0\0GNU\0\0\0\0\0\2\0\0\0\2\0\0\0"..., 32) = 32
[pid  9216] fstat64(8, {st_mode=S_IFREG|0644, st_size=2108, ...}) = 0
[pid  9216] old_mmap(NULL, 5588, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 8, 0) = 0x b658f000
[pid  9216] old_mmap(0xb6590000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENY WRITE, 8, 0) = 0xb6590000
[pid  9216] close(8)                    = 0
[pid  9216] mprotect(0xb658f000, 4096, PROT_READ|PROT_WRITE) = 0
[pid  9216] mprotect(0xb658f000, 4096, PROT_READ|PROT_EXEC) = 0
[pid  9216] mprotect(0xb6591000, 7548928, PROT_READ|PROT_WRITE) = 0
[pid  9216] mprotect(0xb6591000, 7548928, PROT_READ|PROT_EXEC) = 0
[pid  9216] mprotect(0xb6cfa000, 417792, PROT_READ|PROT_WRITE) = 0
[pid  9216] mprotect(0xb6cfa000, 417792, PROT_READ|PROT_EXEC) = 0
[pid  9216] munmap(0xb6d79000, 71208)   = 0
[pid  9216] open("/dev/zero", O_RDWR)   = 8
[pid  9216] mmap2(NULL, 8192, PROT_READ|PROT_WRITE|PROT_EXEC, MAP_PRIVATE, 8, 0) = 0xb6d890 00
[pid  9216] close(8)                    = 0
[pid  9216] mmap2(NULL, 372736, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0 xb6534000
[pid  9216] --- SIGSEGV (Segmentation fault) @ 0 (0) ---
[pid  9216] --- SIGSEGV (Segmentation fault) @ 0 (0) ---
[pid  9217] <... futex resumed> )       = -1 EINTR (Interrupted system call)
[pid  9217] +++ killed by SIGSEGV +++
+++ killed by SIGSEGV +++

```

These are the last 80 lines or so.....

So. NVidia driver or what????

---

### Post by obscenic on 2007-11-16
I am having serious audio issues with XMMS after the upgrade.  It starts and runs fine, but anytime I try and do anything that needs graphic/cpu cycles (loading websites, dragging windows, minimizing and maximizing etc), it skips and warps the audio output.

---

