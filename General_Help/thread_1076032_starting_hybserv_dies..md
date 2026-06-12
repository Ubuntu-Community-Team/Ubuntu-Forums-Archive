---
title: "starting hybserv dies."
date: 2009-02-20
forum: General Help
---

### Post by NukEvil on 2009-02-20
Get this error when trying to start hybserv after a new install:

nukevil@serv:/usr/local/hybserv$ ./hybserv
Hybserv2 TS services version 1.9.3-release by Hybserv2 team
Compiled at Feb 20 2009, 21:47:35
Unable to open SETPATH (/usr/local/hybserv/settings.conf)


Any ideas?  I see nothing to do with SETPATH in settings.conf...

OS is ubuntu server edition
IRC is ircd-hybrid, with (broken) hybserv install.

---

### Post by NukEvil on 2009-02-21
ttt

---

### Post by NukEvil on 2009-02-22
nukevil@serv:/etc/hybserv$ sudo strace hybserv
execve("/usr/sbin/hybserv", ["hybserv"], [/* 14 vars */]) = 0
brk(0)                                  = 0x9702000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7fce000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=21028, ...}) = 0
mmap2(NULL, 21028, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7fc8000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libcrypt.so.1", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0 \7\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=38300, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7fc7000
mmap2(NULL, 201052, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7f95000
mmap2(0xb7f9e000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x8) = 0xb7f9e000
mmap2(0xb7fa0000, 155996, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7fa0000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\340g\1"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=1425800, ...}) = 0
mmap2(NULL, 1431152, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7e37000
mmap2(0xb7f8f000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x158) = 0xb7f8f000
mmap2(0xb7f92000, 9840, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7f92000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7e36000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb7e366b0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0xb7f8f000, 8192, PROT_READ)   = 0
mprotect(0xb7f9e000, 4096, PROT_READ)   = 0
mprotect(0xb7fea000, 4096, PROT_READ)   = 0
munmap(0xb7fc8000, 21028)               = 0
time(NULL)                              = 1235360416
umask(077)                              = 022
write(2, "Hybserv2 TS services version 1.9"..., 95Hybserv2 TS services version 1.9.2-debian-4 by Hybserv2 team
Compiled at Nov  8 2006, 14:26:32
) = 95
brk(0)                                  = 0x9702000
brk(0x9723000)                          = 0x9723000
open("/etc/hybserv/settings.conf", O_RDONLY|O_LARGEFILE) = 3
fstat64(3, {st_mode=S_IFREG|0660, st_size=26441, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7fcd000
read(3, "# This file contains many run-ti"..., 4096) = 4096
read(3, "################################"..., 4096) = 4096
read(3, "###############\n\n# NickNameExpir"..., 4096) = 4096
read(3, "his\n# option helps to avoid cata"..., 4096) = 4096
read(3, " is a SuperOp or higher opped on"..., 4096) = 4096
read(3, "ter a connection to\n# a hub serv"..., 4096) = 4096
read(3, " all channel activity as well\n# "..., 4096) = 1865
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb7fcd000, 4096)                = 0
open("/var/run/ircd/hybserv.pid", O_RDONLY|O_LARGEFILE) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7fcd000
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb7fcd000, 4096)                = 0
getuid32()                              = 0
geteuid32()                             = 0
write(2, "FATAL: Please don\'t run services"..., 55FATAL: Please don't run services as root. Now exiting.
) = 55
exit_group(1)                           = ?
Process 5866 detached
nukevil@serv:/etc/hybserv$

---

### Post by cyclobs on 2009-06-20
probably a Wayyyyyyyy old replay.

it's a permissions issue. hybserv cannot read the settings.conf so thats why you are receiving the error. all i did was allow everything to read only and that seems to work. probably not the best idea tho

---

