---
title: "Error when I launch Enemy Territory"
date: 2005-05-09
forum: Gaming &amp; Leisure
---

### Post by SwanMocker on 2005-05-09
I get this error whenever I try to launch ET.

mocker@ubuntu:~$ et
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/mocker/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 16 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect


***********************************************************
 You are using software Mesa (no hardware acceleration)!
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Received signal 11, exiting...

---

### Post by SwanMocker on 2005-05-09
Ok turns out all I needed was to do a proper reboot...makes me feel silly considering all the stuff I tried doing...

---

### Post by mast on 2005-05-18
I've got a similar problem, but a reboot certainly doesn't fix it for me. I get the SIGSEGV a bit sooner, though:

```
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/mast/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Received signal 11, exiting...
``` 

Using AMD64 arch and NVidia drivers.

Judging from strace, it does open the right 32 bit libs:

```
write(2, "...loading libGL.so.1: ", 23...loading libGL.so.1: ) = 23
open("./tls/i686/mmx/cmov/libGL.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./tls/i686/mmx/libGL.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./tls/i686/cmov/libGL.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./tls/i686/libGL.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./tls/mmx/cmov/libGL.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./tls/mmx/libGL.so.1", O_RDONLY)  = -1 ENOENT (No such file or directory)
open("./tls/cmov/libGL.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./tls/libGL.so.1", O_RDONLY)      = -1 ENOENT (No such file or directory)
open("./i686/mmx/cmov/libGL.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./i686/mmx/libGL.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./i686/cmov/libGL.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./i686/libGL.so.1", O_RDONLY)     = -1 ENOENT (No such file or directory)
open("./mmx/cmov/libGL.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./mmx/libGL.so.1", O_RDONLY)      = -1 ENOENT (No such file or directory)
open("./cmov/libGL.so.1", O_RDONLY)     = -1 ENOENT (No such file or directory)
open("./libGL.so.1", O_RDONLY)          = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 7
fstat64(0x7, 0xffffc6dc)                = 0
old_mmap(0xe4a900000000, 8589934593, PROT_READ|PROT_WRITE|PROT_EXEC, 0xf /* MAP_??? */|MAP_FIXED|MAP_ANONYMOUS|MAP_NORESERVE|MAP_POPULATE|MAP_NONBLOCK|MAP_GROWSDOWN|MAP_DENYWRITE|MAP_EXECUTABLE|MAP_LOCKED|0xfffe06c0, 65025, 0x158d0b081ad815) = 0x5c074000
close(7)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib32/libGL.so.1", O_RDONLY) = 7
read(7, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260K\2"..., 512) = 512
fstat64(0x7, 0xffffc78c)                = 0
old_mmap(0x77dc000000000, 8589934597, PROT_READ|PROT_WRITE|PROT_EXEC, MAP_FILE|MAP_GROWSDOWN|MAP_LOCKED|0x94606c0, 22, 0x2fffc74800000016) = 0x5c083000
old_mmap(0x170005c0e3000, 77309411335, PROT_READ|PROT_WRITE|PROT_EXEC, MAP_FILE|MAP_GROWSDOWN|MAP_LOCKED|0x94606c0, 22, 0x2fffc74800000016) = 0x5c0e3000
old_mmap(0xdc05c0fa000, 214748364807, PROT_READ|PROT_WRITE|PROT_EXEC|PROT_SEM|PROT_GROWSDOWN|PROT_GROWSUP|0xfcfffff0, MAP_FILE|MAP_GROWSDOWN|MAP_LOCKED|0x94606c0, 22, 0x2fffc74800000016) = 0x5c0fa000
close(7)                                = 0
open("./tls/i686/mmx/cmov/libGLcore.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./tls/i686/mmx/libGLcore.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./tls/i686/cmov/libGLcore.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./tls/i686/libGLcore.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./tls/mmx/cmov/libGLcore.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./tls/mmx/libGLcore.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./tls/cmov/libGLcore.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./tls/libGLcore.so.1", O_RDONLY)  = -1 ENOENT (No such file or directory)
open("./i686/mmx/cmov/libGLcore.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./i686/mmx/libGLcore.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./i686/cmov/libGLcore.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./i686/libGLcore.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./mmx/cmov/libGLcore.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./mmx/libGLcore.so.1", O_RDONLY)  = -1 ENOENT (No such file or directory)
open("./cmov/libGLcore.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./libGLcore.so.1", O_RDONLY)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib32/libGLcore.so.1", O_RDONLY) = 7
read(7, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\300H\v"..., 512) = 512
fstat64(0x7, 0xffffc58c)                = 0
old_mmap(0x750ba800000000, 8589934597, PROT_READ|PROT_WRITE|PROT_EXEC, 0x8 /* MAP_??? */|MAP_DENYWRITE|MAP_LOCKED|0x9460240, 26, 0x2fffd5cf0000001a) = 0x5c0fb000
old_mmap(0x1c0005c81c000, 77309411331, PROT_READ|PROT_WRITE|PROT_EXEC, 0x8 /* MAP_??? */|MAP_DENYWRITE|MAP_LOCKED|0x9460240, 26, 0x2fffd5cf0000001a) = 0x5c81c000
old_mmap(0x13ba85c838000, 214748364803, PROT_READ|PROT_WRITE|PROT_EXEC|PROT_SEM|PROT_GROWSDOWN|PROT_GROWSUP|0xfcfffff0, 0x8 /* MAP_??? */|MAP_DENYWRITE|MAP_LOCKED|0x9460240, 26, 0x2fffd5cf0000001a) = 0x5c838000
close(7)                                = 0
open("./tls/i686/mmx/cmov/libnvidia-tls.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./tls/i686/mmx/libnvidia-tls.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./tls/i686/cmov/libnvidia-tls.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./tls/i686/libnvidia-tls.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./tls/mmx/cmov/libnvidia-tls.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./tls/mmx/libnvidia-tls.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./tls/cmov/libnvidia-tls.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./tls/libnvidia-tls.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./i686/mmx/cmov/libnvidia-tls.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./i686/mmx/libnvidia-tls.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./i686/cmov/libnvidia-tls.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./i686/libnvidia-tls.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./mmx/cmov/libnvidia-tls.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./mmx/libnvidia-tls.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./cmov/libnvidia-tls.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./libnvidia-tls.so.1", O_RDONLY)  = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib32/libnvidia-tls.so.1", O_RDONLY) = 7
read(7, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0 \3\0\000"..., 512) = 512
lseek(7, 1272, SEEK_SET)                = 1272
read(7, "\4\0\0\0\20\0\0\0\1\0\0\0GNU\0\0\0\0\0\2\0\0\0\2\0\0\0"..., 32) = 32
fstat64(0x7, 0xffffc570)                = 0
old_mmap(0x15b400000000, 8589934597, PROT_READ|PROT_WRITE|PROT_EXEC, 0xe /* MAP_??? */|MAP_FIXED, 4, 0x5555e10dffffc4bc) = 0x5c84c000
old_mmap(0x10005c84d000, 77309411331, PROT_READ|PROT_WRITE|PROT_EXEC, 0xe /* MAP_??? */|MAP_FIXED, 4, 0x5555e10dffffc4bc) = 0x5c84d000
close(7)                                = 0
mprotect(0x5c84c000, 4096, PROT_READ|PROT_WRITE) = 0
mprotect(0x5c84c000, 4096, PROT_READ|PROT_EXEC) = 0
mprotect(0x5c0fb000, 7475200, PROT_READ|PROT_WRITE) = 0
mprotect(0x5c0fb000, 7475200, PROT_READ|PROT_EXEC) = 0
mprotect(0x5c083000, 393216, PROT_READ|PROT_WRITE) = 0
mprotect(0x5c083000, 393216, PROT_READ|PROT_EXEC) = 0
munmap(0x5c074000, 58537)               = 0
open("/dev/zero", O_RDWR)               = 7
mmap2(NULL, 8192, PROT_READ|PROT_WRITE|PROT_EXEC, 0x7 /* MAP_??? */, 2, 0x7) = 0x5c074000
close(7)                                = 0
getpid()                                = 9569
mmap2(NULL, 622592, PROT_READ|PROT_WRITE, 0x3 /* MAP_??? */, 34, 0xffffffff) = 0x5c84e000
getpid()                                = 9569
modify_ldt(0x11, 0xffffc97c, 0x10)      = 0
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
fstat64(0x1, 0xffffbfa4)                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, 0x3 /* MAP_??? */, 34, 0xffffffff) = 0x5c8e6000
write(1, "Received signal 11, exiting...\n", 31Received signal 11, exiting...
) = 31
futex(0x557b07e0, FUTEX_WAKE, 1)        = 0
getpid()                                = 9569
```

---

### Post by mrbass on 2005-05-19
mast read this for amd64
[http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)

---

### Post by mast on 2005-05-19
Thanks for the tip. It helped a bit, even though it looked like it found the proper 32 bit emulation libs in the first place. Now it stops at the sound initialization, but I guess it's just some sort of chroot thingie.

---

### Post by mrbass on 2005-05-22
killall -9 esd 
before ya start et

---

### Post by h4ck3r on 2005-06-02
I get the same error that the first guy had except a reboot doesn't fix it. ](*,) It runs when you put in "+set r_allowSoftwareGL 1" but realy slowly :(.

---

