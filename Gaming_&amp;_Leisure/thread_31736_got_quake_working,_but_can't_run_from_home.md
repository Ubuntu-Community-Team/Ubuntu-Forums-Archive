---
title: "got quake working, but can't run from /home"
date: 2005-05-04
forum: Gaming &amp; Leisure
---

### Post by railz68 on 2005-05-04
If I open terminal and goto /usr/local/games/quake, it runs.
Doing the same thing from /home/me , it won't. Enemy Territory is also under /usr/local/games, and I can launch that from home.
Also, quake isn't creating a .quake  (like .etwolf), for saves and what not. Each time it's launched, it doesn't remember custom settings (keyboard keys, brightness,....). Do you need to create a ".quake" directory for it ?.
Created sym link to it, still no go. Thanks for any info u may have on this.

Here is error:
quake
Error: W_LoadWadFile: couldn't load gfx.wad

and "strace quake" 
[PHP]
strace quake

execve("/usr/bin/quake", ["quake"], [/* 31 vars */]) = 0
uname({sys="Linux", node="ubuntu", ...}) = 0
brk(0)                                  = 0xa8d6000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
old_mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7fe9000
open("/etc/ld.so.preload", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=60548, ...}) = 0
old_mmap(NULL, 60548, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7fda000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libm.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\0006\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=130432, ...}) = 0
old_mmap(NULL, 132928, PROT_READ|PROT_EXEC, MAP_PRIVATE, 3, 0) = 0xb7fb9000
old_mmap(0xb7fd9000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED, 3, 0x1f000) = 0xb7fd9000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libdl.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\276\31"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=9152, ...}) = 0
old_mmap(NULL, 12008, PROT_READ|PROT_EXEC, MAP_PRIVATE, 3, 0) = 0xb7fb6000
old_mmap(0xb7fb8000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED, 3, 0x1000) = 0xb7fb8000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libGL.so.1", O_RDONLY)   = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260K\2"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=482256, ...}) = 0
old_mmap(NULL, 490944, PROT_READ|PROT_EXEC, MAP_PRIVATE, 3, 0) = 0xb7f3e000
old_mmap(0xb7f9e000, 94208, PROT_READ|PROT_WRITE|PROT_EXEC, MAP_PRIVATE|MAP_FIXED, 3, 0x5f000) = 0xb7f9e000
old_mmap(0xb7fb5000, 3520, PROT_READ|PROT_WRITE|PROT_EXEC, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7fb5000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/X11R6/lib/libX11.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\220\25"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=802576, ...}) = 0
old_mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f3d000
old_mmap(NULL, 806872, PROT_READ|PROT_EXEC, MAP_PRIVATE, 3, 0) = 0xb7e78000
old_mmap(0xb7f39000, 16384, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED, 3, 0xc0000) = 0xb7f39000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/X11R6/lib/libXext.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\220)\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=51760, ...}) = 0
old_mmap(NULL, 51028, PROT_READ|PROT_EXEC, MAP_PRIVATE, 3, 0) = 0xb7e6b000
old_mmap(0xb7e77000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED, 3, 0xc000) = 0xb7e77000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\215Y\1"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=1222116, ...}) = 0
old_mmap(NULL, 1232428, PROT_READ|PROT_EXEC, MAP_PRIVATE, 3, 0) = 0xb7d3e000
old_mmap(0xb7e60000, 36864, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED, 3, 0x121000) = 0xb7e60000
old_mmap(0xb7e69000, 7724, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7e69000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libGLcore.so.1", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\300H\v"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=7583764, ...}) = 0
old_mmap(NULL, 7670696, PROT_READ|PROT_EXEC, MAP_PRIVATE, 3, 0) = 0xb75ed000
old_mmap(0xb7d0e000, 114688, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED, 3, 0x720000) = 0xb7d0e000
old_mmap(0xb7d2a000, 80808, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7d2a000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/libnvidia-tls.so.1", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20\3\0"..., 512) = 512
lseek(3, 980, SEEK_SET)                 = 980
read(3, "\4\0\0\0\20\0\0\0\1\0\0\0GNU\0\0\0\0\0\2\0\0\0\3\0\0\0"..., 32) = 32
fstat64(3, {st_mode=S_IFREG|0644, st_size=1836, ...}) = 0
old_mmap(NULL, 5268, PROT_READ|PROT_EXEC, MAP_PRIVATE, 3, 0) = 0xb75eb000
old_mmap(0xb75ec000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED, 3, 0) = 0xb75ec000
close(3)                                = 0
old_mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb75ea000
mprotect(0xb75eb000, 4096, PROT_READ|PROT_WRITE) = 0
mprotect(0xb75eb000, 4096, PROT_READ|PROT_EXEC) = 0
mprotect(0xb75ed000, 7475200, PROT_READ|PROT_WRITE) = 0
mprotect(0xb75ed000, 7475200, PROT_READ|PROT_EXEC) = 0
mprotect(0xb7f3e000, 393216, PROT_READ|PROT_WRITE) = 0
mprotect(0xb7f3e000, 393216, PROT_READ|PROT_EXEC) = 0
set_thread_area({entry_number:-1 -> 6, base_addr:0xb75ea5c0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
munmap(0xb7fda000, 60548)               = 0
brk(0)                                  = 0xa8d6000
brk(0xa8f7000)                          = 0xa8f7000
open("/dev/zero", O_RDWR)               = 3
mmap2(NULL, 8192, PROT_READ|PROT_WRITE|PROT_EXEC, MAP_PRIVATE, 3, 0) = 0xb7fe7000
close(3)                                = 0
getpid()                                = 8242
mmap2(NULL, 622592, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7552000
getpid()                                = 8242
rt_sigaction(SIGFPE, {SIG_IGN}, {SIG_DFL}, 8) = 0
fcntl64(0, F_GETFL)                     = 0x2 (flags O_RDWR)
fcntl64(0, F_SETFL, O_RDWR|O_NONBLOCK)  = 0
mmap2(NULL, 16781312, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6551000
getcwd("/home/paul", 127)               = 11
open("/home/paul/id1/pak0.pak", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/home/paul/fuhquake/pak0.pak", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/home/paul/qw/pak0.pak", O_RDONLY) = -1 ENOENT (No such file or directory)open("/home/paul/qw/gfx/pop.lmp", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/home/paul/fuhquake/gfx/pop.lmp", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/home/paul/id1/gfx/pop.lmp", O_RDONLY) = -1 ENOENT (No such file or directory)
getpid()                                = 8242
getuid32()                              = 1000
time(NULL)                              = 1115226574
open("./fuhquake-security.so", O_RDONLY) = -1 ENOENT (No such file or directory)open("/home/paul/qw/gfx.wad", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/home/paul/fuhquake/gfx.wad", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/home/paul/id1/gfx.wad", O_RDONLY) = -1 ENOENT (No such file or directory)fcntl64(0, F_GETFL)                     = 0x802 (flags O_RDWR|O_NONBLOCK)
fcntl64(0, F_SETFL, O_RDWR)             = 0
write(2, "Error: W_LoadWadFile: couldn\'t l"..., 44Error: W_LoadWadFile: couldn't load gfx.wad
) = 44
getpid()                                = 8242
getpid()                                = 8242
getpid()                                = 8242
getpid()                                = 8242
munmap(0xb7552000, 622592)              = 0
munmap(0xb7fe7000, 8192)                = 0
exit_group(1)                           = ?[/PHP]

Only thing I can tell from this, 1st line mentions (/usr/bin/quake). Of course it's not there, but looking in that dir, there is no "et or etwolf" and it does run. 
Also, looking through the quake sub directorys, there is no "gfx.wad" file at all. Yet entering quake from it's own diretory runs fine  ](*,)

---

