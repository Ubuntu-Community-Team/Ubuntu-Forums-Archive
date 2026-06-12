---
title: "firefox keeps segfaulting"
date: 2009-02-24
forum: General Help
---

### Post by Xbehave on 2009-02-24
last thing was updat, install debsums, then update prelink since then alot of my programs segfault
*firefox
*/opt/firefox/firefox <-minefiled
*kalarm
*kmplayer
*kdesktop

i have tried everything to fix this, but have no idea. 
My hdd has been playing up but i debsums shows that most files are fine
MY ram was tested using memtesester (only first 5 tests as i got booard)



here are some gdb errors
kalarm
> Program received signal SIGSEGV, Segmentation fault.
0x00007f208f21da1a in do_lookup_x () from /lib64/ld-linux-x86-64.so.2
(gdb) bt full
#0  0x00007f208f21da1a in do_lookup_x () from /lib64/ld-linux-x86-64.so.2
No symbol table info available.
#1  0x00007f208f21dc6f in _dl_lookup_symbol_x () from /lib64/ld-linux-x86-64.so.2
No symbol table info available.
#2  0x00007f208f21f6ba in _dl_relocate_object () from /lib64/ld-linux-x86-64.so.2
No symbol table info available.
#3  0x00007f208f2179ef in dl_main () from /lib64/ld-linux-x86-64.so.2
No symbol table info available.
#4  0x00007f208f228818 in _dl_sysdep_start () from /lib64/ld-linux-x86-64.so.2
No symbol table info available.
#5  0x00007f208f21630b in _dl_start () from /lib64/ld-linux-x86-64.so.2
No symbol table info available.
#6  0x00007f208f214a68 in _start () from /lib64/ld-linux-x86-64.so.2
No symbol table info available.
#7  0x0000000000000001 in ?? ()
No symbol table info available.
#8  0x00007fff97432793 in ?? ()
No symbol table info available.
#9  0x0000000000000000 in ?? ()
No symbol table info available.


firefox
> Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0x7f808e4c96f0 (LWP 5901)]
0x00007f808e2d6a1a in do_lookup_x () from /lib64/ld-linux-x86-64.so.2
(gdb) bt full
#0  0x00007f808e2d6a1a in do_lookup_x () from /lib64/ld-linux-x86-64.so.2
No symbol table info available.
#1  0x00007f808e2d6c6f in _dl_lookup_symbol_x () from /lib64/ld-linux-x86-64.so.2
No symbol table info available.
#2  0x00007f808e2d86ba in _dl_relocate_object () from /lib64/ld-linux-x86-64.so.2
No symbol table info available.
#3  0x00007f808e2df178 in dl_open_worker () from /lib64/ld-linux-x86-64.so.2
No symbol table info available.
#4  0x00007f808e2dadf6 in _dl_catch_error () from /lib64/ld-linux-x86-64.so.2
No symbol table info available.
#5  0x00007f808e2de91b in _dl_open () from /lib64/ld-linux-x86-64.so.2
No symbol table info available.
#6  0x00007f808deadf8b in dlopen_doit () from /lib/libdl.so.2
No symbol table info available.
#7  0x00007f808e2dadf6 in _dl_catch_error () from /lib64/ld-linux-x86-64.so.2
No symbol table info available.
#8  0x00007f808deae4ed in _dlerror_run () from /lib/libdl.so.2
No symbol table info available.
#9  0x00007f808deadef1 in dlopen@@GLIBC_2.2.5 () from /lib/libdl.so.2
No symbol table info available.
#10 0x00007f808c85cccd in PR_LoadLibraryWithFlags () from /usr/lib/libnspr4.so.0d
No symbol table info available.
#11 0x00007f808c85cd90 in PR_LoadLibrary () from /usr/lib/libnspr4.so.0d
No symbol table info available.
#12 0x00007f808b867b65 in ?? () from /usr/lib/xulrunner-1.9.0.6/libxul.so
No symbol table info available.
#13 0x00007f808b861def in XRE_main () from /usr/lib/xulrunner-1.9.0.6/libxul.so
No symbol table info available.
#14 0x00000000004014f7 in ?? ()
No symbol table info available.
#15 0x00007f808d3cf1c4 in __libc_start_main () from /lib/libc.so.6
No symbol table info available.
#16 0x00000000004010f9 in ?? ()
No symbol table info available.
#17 0x00007fff964e8a08 in ?? ()
No symbol table info available.
#18 0x0000000000000000 in ?? ()
No symbol table info available.

all ideas welcome

---

### Post by Xbehave on 2009-02-25
i removed prelink (purge) 
then i did sudo aptitude reinstall libc6 libc6-dbg libc6-i386 kalarm
because ubottu said File ld-linux-x86-64.so.2 is found in libc6, libc6-dbg

but this still gives the same segfaults :???:

---

### Post by NoaHall on 2009-12-05
Check your RAM. Sounds like a RAM-based problem.

Also -
```
sudo ldconfig && sudo updatedb
```
Might fix a few problems.

---

