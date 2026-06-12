---
title: "libstartup-notification0"
date: 2006-06-23
forum: Desktop Environments
---

### Post by dibblego on 2006-06-23
I am attempting to run OpenOffice 2.0.2 on Ubuntu 6.06/GNOME
I ran into the problem described at [http://dot.kde.org/1101482981/1103495880/1103522538/1103548250/1105981037/1115076593/](http://dot.kde.org/1101482981/1103495880/1103522538/1103548250/1105981037/1115076593/)
I cannot seem to remedy this problem.
To demonstrate my problem in more precise detail, see below - any assistance is most appreciated.

tmorris@fjr:~$ ooffice
no suitable windowing system found, exiting.

** (process:31591): WARNING **: Unknown error forking main binary / abnormal early exit ...
tmorris@fjr:~$ sudo apt-get install libstartup-notification0
Reading package lists... Done
Building dependency tree... Done
libstartup-notification0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up libgtk2.0-bin (2.8.18-0ubuntu1) ...
Updating the IM modules list for GTK+-2.4.0...done.
Updating the gdk-pixbuf loaders list for GTK+-2.4.0.../usr/sbin/update-gdkpixbuf-loaders: line 25: 31630 Segmentation fault      /usr/bin/gdk-pixbuf-query-loaders >$TMPFILE
dpkg: error processing libgtk2.0-bin (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 libgtk2.0-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)
tmorris@fjr:~$ sudo gdk-pixbuf-query-loaders
# GdkPixbuf Image Loader Modules file
# Automatically generated file, do not edit
# Created by gdk-pixbuf-query-loaders from gtk+-2.8.18
#
# LoaderDir = /usr/lib/gtk-2.0/2.4.0/loaders
#
Segmentation fault

---

### Post by dibblego on 2006-06-23
Here is the output of strace gdk-pixbuf-query-loaders 

execve("/usr/bin/gdk-pixbuf-query-loaders", ["gdk-pixbuf-query-loaders"], [/* 36 vars */]) = 0
uname({sys="Linux", node="fjr", ...})   = 0
brk(0)                                  = 0x804b000
old_mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7fca000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
old_mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7fc8000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=49575, ...}) = 0
old_mmap(NULL, 49575, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7fbb000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libgdk_pixbuf-2.0.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0`7\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=84616, ...}) = 0
old_mmap(NULL, 83544, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7fa6000
old_mmap(0xb7fba000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x14000) = 0xb7fba000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libgmodule-2.0.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0p\r\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=9768, ...}) = 0
old_mmap(NULL, 8720, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7fa3000
old_mmap(0xb7fa5000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2000) = 0xb7fa5000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libdl.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260\v\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=8204, ...}) = 0
old_mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7fa2000
old_mmap(NULL, 11016, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7f9f000
old_mmap(0xb7fa1000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1000) = 0xb7fa1000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libgobject-2.0.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0@j\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=229092, ...}) = 0
old_mmap(NULL, 229316, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7f67000
old_mmap(0xb7f9e000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x37000) = 0xb7f9e000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libglib-2.0.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000\305"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=535424, ...}) = 0
old_mmap(NULL, 539020, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7ee3000
old_mmap(0xb7f66000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x82000) = 0xb7f66000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libm.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0@3\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=136368, ...}) = 0
old_mmap(NULL, 138800, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7ec1000
old_mmap(0xb7ee2000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x20000) = 0xb7ee2000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\220O\1"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=1232784, ...}) = 0
old_mmap(NULL, 1238972, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7d92000
old_mmap(0xb7eb7000, 28672, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x125000) = 0xb7eb7000
old_mmap(0xb7ebe000, 10172, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7ebe000
close(3)                                = 0
old_mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7d91000
old_mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7d90000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb7d906c0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
munmap(0xb7fbb000, 49575)               = 0
fstat64(1, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 0), ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7fc7000
write(1, "# GdkPixbuf Image Loader Modules"..., 38) = 38
write(1, "# Automatically generated file, "..., 44) = 44
write(1, "# Created by gdk-pixbuf-query-lo"..., 57) = 57
write(1, "# LoaderDir = /usr/lib/gtk-2.0/2"..., 47) = 47
brk(0)                                  = 0x804b000
brk(0x806c000)                          = 0x806c000
open("/usr/lib/gtk-2.0/2.4.0/loaders", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = 3
fstat64(3, {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
getdents64(3, /* 18 entries */, 4096)   = 792
gettimeofday({1151057130, 284815}, NULL) = 0
stat64("/usr/lib/gtk-2.0/2.4.0/loaders/io-wmf.so", {st_mode=S_IFREG|0644, st_size=6180, ...}) = 0
open("/usr/lib/gtk-2.0/2.4.0/loaders/io-wmf.so", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\244\t\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=6180, ...}) = 0
old_mmap(NULL, 9192, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb7fc4000
old_mmap(0xb7fc6000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x1000) = 0xb7fc6000
close(4)                                = 0
open("/etc/ld.so.cache", O_RDONLY)      = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=49575, ...}) = 0
old_mmap(NULL, 49575, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb7d83000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libwmf-0.2.so.7", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\240g\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=309924, ...}) = 0
old_mmap(NULL, 325476, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb7d33000
old_mmap(0xb7d5f000, 131072, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x2c000) = 0xb7d5f000
old_mmap(0xb7d7f000, 14180, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7d7f000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/sse2/cmov/libwmflite-0.2.so.7", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/tls/i686/sse2/cmov", 0xbfcdea14) = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/sse2/libwmflite-0.2.so.7", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/tls/i686/sse2", 0xbfcdea14) = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libwmflite-0.2.so.7", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/tls/i686/cmov", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/lib/tls/i686/libwmflite-0.2.so.7", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/tls/i686", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/lib/tls/sse2/cmov/libwmflite-0.2.so.7", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/tls/sse2/cmov", 0xbfcdea14) = -1 ENOENT (No such file or directory)
open("/lib/tls/sse2/libwmflite-0.2.so.7", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/tls/sse2", 0xbfcdea14)     = -1 ENOENT (No such file or directory)
open("/lib/tls/cmov/libwmflite-0.2.so.7", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/tls/cmov", 0xbfcdea14)     = -1 ENOENT (No such file or directory)
open("/lib/tls/libwmflite-0.2.so.7", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/tls", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/lib/i686/sse2/cmov/libwmflite-0.2.so.7", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i686/sse2/cmov", 0xbfcdea14) = -1 ENOENT (No such file or directory)
open("/lib/i686/sse2/libwmflite-0.2.so.7", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i686/sse2", 0xbfcdea14)    = -1 ENOENT (No such file or directory)
open("/lib/i686/cmov/libwmflite-0.2.so.7", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i686/cmov", 0xbfcdea14)    = -1 ENOENT (No such file or directory)
open("/lib/i686/libwmflite-0.2.so.7", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i686", 0xbfcdea14)         = -1 ENOENT (No such file or directory)
open("/lib/sse2/cmov/libwmflite-0.2.so.7", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/sse2/cmov", 0xbfcdea14)    = -1 ENOENT (No such file or directory)
open("/lib/sse2/libwmflite-0.2.so.7", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/sse2", 0xbfcdea14)         = -1 ENOENT (No such file or directory)
open("/lib/cmov/libwmflite-0.2.so.7", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/cmov", 0xbfcdea14)         = -1 ENOENT (No such file or directory)
open("/lib/libwmflite-0.2.so.7", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/usr/lib/tls/i686/sse2/cmov/libwmflite-0.2.so.7", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/tls/i686/sse2/cmov", 0xbfcdea14) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/i686/sse2/libwmflite-0.2.so.7", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/tls/i686/sse2", 0xbfcdea14) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/i686/cmov/libwmflite-0.2.so.7", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/tls/i686/cmov", 0xbfcdea14) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/i686/libwmflite-0.2.so.7", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/tls/i686", 0xbfcdea14) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/sse2/cmov/libwmflite-0.2.so.7", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/tls/sse2/cmov", 0xbfcdea14) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/sse2/libwmflite-0.2.so.7", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/tls/sse2", 0xbfcdea14) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/cmov/libwmflite-0.2.so.7", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/tls/cmov", 0xbfcdea14) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/libwmflite-0.2.so.7", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/tls", 0xbfcdea14)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i686/sse2/cmov/libwmflite-0.2.so.7", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i686/sse2/cmov", 0xbfcdea14) = -1 ENOENT (No such file or directory)
open("/usr/lib/i686/sse2/libwmflite-0.2.so.7", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i686/sse2", 0xbfcdea14) = -1 ENOENT (No such file or directory)
open("/usr/lib/i686/cmov/libwmflite-0.2.so.7", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i686/cmov", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/usr/lib/i686/libwmflite-0.2.so.7", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i686", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/usr/lib/sse2/cmov/libwmflite-0.2.so.7", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/sse2/cmov", 0xbfcdea14) = -1 ENOENT (No such file or directory)
open("/usr/lib/sse2/libwmflite-0.2.so.7", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/sse2", 0xbfcdea14)     = -1 ENOENT (No such file or directory)
open("/usr/lib/cmov/libwmflite-0.2.so.7", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/cmov", 0xbfcdea14)     = -1 ENOENT (No such file or directory)
open("/usr/lib/libwmflite-0.2.so.7", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\220.\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=105164, ...}) = 0
old_mmap(NULL, 108180, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb7d18000
old_mmap(0xb7d32000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x19000) = 0xb7d32000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libfreetype.so.6", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000k\0\000"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=430292, ...}) = 0
old_mmap(NULL, 429152, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb7caf000
old_mmap(0xb7d15000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x66000) = 0xb7d15000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libSM.so.6", O_RDONLY)   = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260\37"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=31328, ...}) = 0
old_mmap(NULL, 30264, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb7fbc000
old_mmap(0xb7fc3000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x7000) = 0xb7fc3000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libICE.so.6", O_RDONLY)  = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0p6\0\000"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=84724, ...}) = 0
old_mmap(NULL, 95024, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb7c97000
old_mmap(0xb7cac000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x14000) = 0xb7cac000
old_mmap(0xb7cad000, 4912, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7cad000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libX11.so.6", O_RDONLY)  = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000I\1\000"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=938112, ...}) = 0
old_mmap(NULL, 938412, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb7bb1000
old_mmap(0xb7c92000, 16384, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0xe1000) = 0xb7c92000
old_mmap(0xb7c96000, 428, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7c96000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libexpat.so.1", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260\"\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=125168, ...}) = 0
old_mmap(NULL, 124076, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb7b92000
old_mmap(0xb7bae000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x1c000) = 0xb7bae000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libjpeg.so.62", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\360\"\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=123372, ...}) = 0
old_mmap(NULL, 126328, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb7b73000
old_mmap(0xb7b91000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x1d000) = 0xb7b91000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libpng12.so.0", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\2009\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=142304, ...}) = 0
old_mmap(NULL, 141204, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb7b50000
old_mmap(0xb7b72000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x22000) = 0xb7b72000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libz.so.1", O_RDONLY)    = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0`\26\0\000"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=77368, ...}) = 0
old_mmap(NULL, 80324, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb7b3c000
old_mmap(0xb7b4f000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x12000) = 0xb7b4f000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libXau.so.6", O_RDONLY)  = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260\t\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=7052, ...}) = 0
old_mmap(NULL, 9996, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb7b39000
old_mmap(0xb7b3b000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x1000) = 0xb7b3b000
close(4)                                = 0
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++

---

